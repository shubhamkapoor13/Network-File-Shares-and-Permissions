<p align="center">
<img src="https://i.imgur.com/npSuccP.png" height="30%" width="30%" alt="Network File"/>
</p>

<h1>Network File Permissions/Shares</h1> 
In this tutorial, I will be showing how to set network file permissions and sharing it with other users. This tutorial will give you a feel for how an Information Technology (IT) Administrator would grant/deny access to users in regards to certain network files and folders. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machines
- Microsoft Remote Desktop
- Windows File Explorer

<h2>Steps</h2>

<h3>Create two virtual machines</h3>
First, you need to create two virtual machines: one will be the domain controller (DC-1) and the other will be a regular client (Client-1). This lab is build off on the Active Directory lab and will be set up the same way.

<p></p>

If you have not done the Active directory lab yet, please go [here](https://github.com/afisaminou/configure-ad).

<p></p>

Log into DC-1 and Client-1 using Microsoft Remote Desktop. For Client-1, log in with a user that was created from the Active Directory lab.

<p>
<img src="https://i.imgur.com/Av5OHCs.png" height="80%" width="80%" alt="1."/>
</p>
  
<p>
<img src="https://i.imgur.com/1arqrs2.png" height="80%" width="80%" alt="2."/>
</p>


<h3>Create Network Folders</h3>
Next, go to the c:/ drive on the DC-1 machine and create 4 folders. Go to Windows File Explorer in the Start Menu and create the following folders:

- read-access
- read/write-access
- no-access
- accounting

<p>
<img src="https://i.imgur.com/9pZ01UW.png" height="80%" width="80%" alt="4."/>
</p>


Next, let's go into each folder and set up permission level for each folders: -> right click the folder -> Prorieties ->  Permission Level -> Share
- read-access -> Add Domain Users -> Read Permissions
- write-access -> Add Domain Users -> Read/Write Permissions
- no-access -> Add Domain Admins -> Read/Write Permissions

<p></p>

Leave the accounting folder for now.

<p>
<img src="https://i.imgur.com/0jhupJZ.png" height="80%" width="80%" alt="6."/>
</p>

<p>
<img src="https://i.imgur.com/SKT0aYj.png" height="80%" width="80%" alt="7."/>
</p>

<p>
<img src="https://i.imgur.com/WikXWFC.png" height="80%" width="80%" alt="8."/>
</p>

<p>
<img src="https://i.imgur.com/lVWxB8C.png" height="80%" width="80%" alt="9."/>
</p>

<p>
<img src="https://i.imgur.com/EsqqGsx.png" height="80%" width="80%" alt="10."/>
</p>

<h3>Using Client-1 to access Network Folders</h3>
Now, go into Client-1. Go into Windows File Explorer and type in "\\dc-1". From here, try to access the folders and observe the results for each one. 

<p>
<img src="https://i.imgur.com/07U1phZ.png" height="80%" width="80%" alt="11."/>
</p>

<p>
<img src="https://i.imgur.com/e4r2ORL.png" height="80%" width="80%" alt="12."/>
</p>

<p>
<img src="https://i.imgur.com/XZ5Nqsb.png" height="80%" width="80%" alt="13."/>
</p>

<p>
<img src="https://i.imgur.com/0EtiZM7.png" height="80%" width="80%" alt="14."/>
</p>

<p>
<img src="https://i.imgur.com/Q75dXmF.png" height="80%" width="80%" alt="15."/>
</p>

<h3>Create a New Group in Active Directory</h3>
Log back into DC-1 and open Active Directory Users and Computers. Then go into the following: mydomain.com (domain that was created) -> _SECURITYGROUPS -> right click in the main window -> New -> Group. Then add "ACCOUNTANTS." Right click "ACCOUNTANTS" -> Properties -> Members -> add the random account you have created.

<p></p>
Next go back into Windows File Explorer. Go accounting folder -> right click -> Properties -> Sharing -> Add ACCOUNTANTS -> Read/Write Permissions.

<p>
<img src="https://i.imgur.com/qalaQBi.png" height="80%" width="80%" alt="16."/>
</p>

<p>
<img src="https://i.imgur.com/Qxd7YaC.png" height="80%" width="80%" alt="17."/>
</p>

<p>
<img src="https://i.imgur.com/4XywO9r.png" height="80%" width="80%" alt="19."/>
</p>


When it is done, go back into Client-1. Then attempt go into the accounting folder and you should be able to.

<p>
<img src="https://i.imgur.com/5IP6i7k.png" height="80%" width="80%" alt="21."/>
</p>


This exercise should have give you some intuition on how to create network files and set the permissions. Thank you checking out my tutorial! 


**REMEMBER TO ALWAYS CLEAN UP YOUR RESOURCES ONCE YOU ARE DONE WITH THE LAB!**
