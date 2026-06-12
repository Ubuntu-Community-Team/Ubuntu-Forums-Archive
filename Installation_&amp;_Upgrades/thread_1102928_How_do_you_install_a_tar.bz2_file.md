---
title: "How do you install a tar.bz2 file"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2009-03-22
How do you install a tar.bz2 file

---

### Post by dandnsmith on 2009-03-22
Depends what is in it,
but the first step is to unpack it with something like:
tar -xvf tarr'ed file > destination_file

Then you may have an install shell script to execute

---

### Post by Mike001977 on 2009-03-22
guys I need help :)

I am so noob in linux.

First so far i delete Windows XP for ever lol 
and i install ubuntu 8.10 cause i want to learn.

so far my PC run perfect after 200000 installation and many crash i did 

Now i have a small problem 

I want to install my UPS console and Drivers 
[http://www.mustek.de/eng_/html/treiber/ups.htm](http://www.mustek.de/eng_/html/treiber/ups.htm)
this is the link i have my file on the desktop.
File end to tar.gz

so consider that i have no idea how to install it and please send me
few instraction 

Thanks.
PS sorry for my english. Greek :)

---

### Post by sgosnell on 2009-03-22
A tar.gz file is an archive, like a .zip file in Windows.  You have to extract the contents and then deal with what is inside.  The files in the archive could be in any format, so the first step is to extract them.  The easy way is to open the file manager, right-click on the file, and click on Extract.  You can then choose where to extract the archive.  What you do then depends on the files you get.

If there is a .deb or .rpm, you can right-click on it and select Install.  If it's a .run or something else, you can perhaps mark it as executable and just run it.  It's possible you may have to compile it.  I looked at the file you linked, but it's 30MB, and I don't have time to download and deal with it right now.

---

### Post by Mike001977 on 2009-03-22
please Advice :(




setup.bin cant execute. 

this is the text in the folder

==================
Install Winpower
==================
        1.  Enter /Linux directory. If system is running in GUI mode, double click setup.bin to start the installation. If system is running in Text mode, execute ./setup_console.bin to start the installation. 
        2.  Read the information provided, then press ENTER to continue .
        3.  When the installation program is completed,reboot the system to set enviroment variables for Winpower(which is set in /etc/profile).

        Note: The installation should be made as "root"!
================     
Run Winpower
================
        1.  Start Agent
	    Winpower Agent will auto start when Linux system start.
            You can also start agent manually by open the terminal and execute command:
            cd /opt/upspilot/
            ./agent start
            
        2.  Start Monitor
            execute command:
            cd /opt/upspilot/
            ./monitor

        3.  Get Full Access
            In "System" menu, click "Act as Administrator" menu item to start the "Administrator" dialog, enter correct password to get full access.
            The default password is set to "Administrator".It can be changed in "Modify Administrator Password" dialog.
          
        4.  Communicate with UPS
            In "System" menu, click "Auto Search UPS" menu item to auto search the UPS connected with Computer.

==============        
Stop Winpower
==============
        1.  Close Manager.
        2.  Open the Terminal, enter install directory:
            and execute command:
            ./agent stop


====================
Uninstall Winpower
====================
 	1.  Open the Terminal, enter install directory:
            and execute command:
            ./Uninstall

---

### Post by sgosnell on 2009-03-22
You need to make setup.bin executable.  In the file manager, right-click on it, select Properties, Permissions, and check the Execute box.  Then you can either double-click on it, or right-click and select Run.  You might need to select Run In Terminal to get output, that's fairly common with these type installation files.

I have to say, that's a very poorly presented program.  Having to do all that in a terminal is just laziness, or ignorance.  You would think a company as large as UPS, which depends on customer loyalty, would do better.

---

### Post by bubwitmaingay on 2009-03-22
Extract or unzip the file (tar.bz2 is an archive).

Usually it will create a folder, then look for a file in the folder that has a filename "INSTALL" or something like that. It is actually a How-To of the installation process. Usually applications packeaged like this are installed using the Terminal.

I have a hard time though of installing them, even with the guide. I think the "alien" command can be used with tar.bz2. This command converts tar.bz2 to .deb making it executable in synaptic.

Hope that helps. 8)

---

