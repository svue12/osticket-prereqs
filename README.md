<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 11</b> (25H2)

<h2>List of Prerequisites</h2>

- Web Server: Apache or IIS.
- PHP Versions:
- Rewrite Module 
- osTicket Version 1.15+
-MySQL Database: 5.5+

<h2>Installation Steps</h2>

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/d38a60b8-fe70-4442-b33a-e496286bfab4)

Part 1 (Create Virtual Machine in Azure)

Create a Resource Group in Azure
Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/b38e3495-dda1-4e37-bb0d-c76cf7f2057f)

Part 2 (Installation)

Install / Enable IIS in Windows with CGI and Common HTTP Features by accessing the "Control Panel" in Windows. Then click on "Programs" and "Turn on Windows features on or off" under "Programs and Features" afterwards.
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/6f5f094c-5e02-414e-8651-bf6935fb3bd1)

Once the window pop-up, click on:

Internet Information Services (drop tab) -> World Wide Web Services -> Application Development Features ->

[X] CGI

[X] Common HTTP Features
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/7d1e8f13-a257-49da-8905-efdd7c1a3358)

Now, enable IIS Management Console by going to:

Internet Information Services -> Web Management Tools ->

[X] IIS Management Console
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/53874a8c-d09a-45f2-b61b-3024c67519cd)

From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP by creating an empty folder inside of Window's Directory (C:) within the "File Explorer" located at the bottom of the screen.


</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/50e8e64c-04ec-4795-8514-8e41332f0455)

From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip or the recommended version) and unzip the contents into C:\PHP

From the Installation Files, download and install VC_redist.x86.exe.

From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi or recommended version). Within the installation, choose the following options when they appear:

Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> (create a password) (as shown below)
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/b8111c2f-5a66-4538-ad20-47a6bf51b69b)

Open IIS as an Admin by entering "ISS" in the search box of the home screen. Select "Run as administrator".
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/04e064e1-270b-468f-adc8-90aa47a5771f)

Select "PHP Manager" once ISS Manager appears and click on "Register new PHP version" to register PHP.
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/c4ef8d36-cff7-4091-9313-937afa4bbf45)

Upload the PHP (C:\PHP) folder that was created previously into entry box.
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/e5c16d65-1058-4715-90e0-c7e357a93c3d)

Open IIS, Stop, and Start the server
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/edf9fd1c-f5a1-4e17-9ae8-bc369a7ae98b)

Part 3 (Install osTicket v1.15.8 or the recommended veerion)

Download osTicket from the Installation Files Folder
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/a63b7ff2-4469-4a34-9c93-0bddbfa3d6e0)

Open IIS, Stop, and Start the server

Under "Connections" on left side of the screen,

Go to sites -> Default -> osTicket -> On the right, click “Browse *:80(http)”
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/b5bdb130-3b2d-4790-b643-6d5f5e80149d)

Some extensions will not be enabled, so:

Go back to IIS, sites -> Default -> osTicket, Double-click "PHP Manager"

Click “Enable or disable an extension”
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/0de10d8b-df87-464d-9cfe-a2c8539c5d88)

Select the following extensions and click "Add" under "Actions" on the right side of the screen.

Enable: php_imap.dll

Enable: php_intl.dll

Enable: php_opcache.dll
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/5ebbbf02-02eb-4e3e-b4e1-7328918a1156)

Go to osTicket site in your browse.
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/ec467017-f979-4de4-9182-d018d910520c)

Return to "File Explorer" to rename: ost-config.php

From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Part 4 (Assign Permissions: ost-config.php)

To change permissions, first disable inheritance:

right click "ost-config" (in File Explore) -> select "Properties" -> "Security" tab at the top -> select the "Advanced" -> "Disable inheritance" -> "Remove All"


</p>
<br />


![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/90320b03-d989-4e32-848e-e026aadce221)![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/4a9cc53d-e3cb-474f-ab69-702cf33cbb60)
![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/fd401115-af38-43f5-ac7d-2a044311f136)


Now apply new permissions:

"Select a principal" -> Under "Enter the object name to select" type "Everyone" -> select "Check Names" -> click "OK" -> seclect "Full Control" under "Basic Permissions" -> "Apply" -> "OK"


</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/afd210cc-d927-45ac-9e5c-f0135d79c739)

From the Installation Files, download and install HeidiSQL.
Open Heidi SQL

</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/24c2c573-3a18-4a64-819b-a4ab30c2ff13)

Create a new session, username, and Password1. For an example, user: root, password: Password1. This information will be entered in osTicket's browser setup.
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/2258a370-40c7-49cd-bdc0-2ea3a3301c57)![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/3f750aa6-935e-4057-a41b-60c8855dae5c)


Connect to the session.
Create a database called “osTicket”
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/23c25411-9470-41c5-b9c0-1cd1cc06d3a9)

Continue Setting up osticket in the browser with information created in Heidi SQL.
MySQL Database: osTicket MySQL Username: root MySQL Password: Password1

After completing the osTicket's setup on the browser, click “Install Now!”
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/9800fe39-a2a7-4e78-bab0-da06528f866a)

Part 5 (Clean up)

Return to "File Explorer" and follow the this directory to delete the following:
Delete: C:\inetpub\wwwroot\osTicket\setup
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/c46de405-9cfb-4f1d-a84c-7d157f72d48f)

Set Permissions to “Read” only by returning to ost-config.php at:
C:\inetpub\wwwroot\osTicket\include\ost-config.php

Next, apply the following settings:
right click "ost-config" (in File Explore) -> select "Properties" -> "Security" tab at the top -> select the "Everyone"
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/89879ab9-a137-4aad-9e7b-a654ac824547)![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/afbb302b-cf82-462a-84ec-e45ccb23fee9)


"Edit" -> remove all checks except for "Read" and "Read & execute -> "OK" -> "Apply" ->"OK
</p>
<br />

![image](https://github.com/JaMyraJones/osticket-prereqs/assets/145633544/676bec80-349c-45eb-a396-2003c3af9bdf)

Browse to your help desk login page: http://localhost/osTicket/scp/login.php
</p>
<br />
