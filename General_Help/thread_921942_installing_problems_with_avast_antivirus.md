---
title: "installing problems with avast antivirus"
date: 2008-09-16
forum: General Help
---

### Post by rocketteer643 on 2008-09-16
downloaded .deb
typed sudo dpkg -i avast4workstation_1.0.8-2_i386.deb in the terminal and recieved the following:
dpkg: error processing avast4workstation_1.0.8-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avast4workstation_1.0.8-2_i386.deb


is there a certain way i need to direct the terminal to the location of the .deb?:confused:

---

### Post by mb_webguy on 2008-09-16
When you type that command, are you in the same directory as the deb package?  When you open the terminal, it starts you in your home directory.  You can change directories with the "cd" command, for example "cd Downloads" or "cd /media/cdrom"

Alternatively, double-clicking on the deb package in Nautilus should open the installer.

---

### Post by kpatz on 2008-09-16
> **rocketteer643 said:**
> downloaded .deb
typed sudo dpkg -i avast4workstation_1.0.8-2_i386.deb in the terminal and recieved the following:
dpkg: error processing avast4workstation_1.0.8-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avast4workstation_1.0.8-2_i386.deb


is there a certain way i need to direct the terminal to the location of the .deb?:confused:Either "cd" to the directory where the .deb file was downloaded, or specify the path to the .deb file when you issue the dpkg command.

For example, if the .deb file is in a downloads directory off your home directory:
```

sudo dpkg -i ~/downloads/avast4workstation_1.0.8-2_i386.deb

```

Also, make sure you spelled the filename correctly.  It looks correct in your post though, but you could still have mistyped it on the command line.  Try copying/pasting the name.

---

### Post by rocketteer643 on 2008-09-17
sudo dpkg -i ~/downloads/avast4workstation_1.0.8-2_i386.deb
dpkg: error processing /home/patrick/downloads/avast4workstation_1.0.8-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/patrick/downloads/avast4workstation_1.0.8-2_i386.deb

and if i just double click the icon it says it is installed but i am unable to find any bit of it

---

### Post by Grabba on 2008-11-10
I double clicked avast4workstation_1.0.8-2_i386.deb to install avast but couldn't find it in any of the menus despite it appearing to have installed ok.

After searching I located avast, avastgui & avast-update files in the folder file system/usr/bin

Used Main Menu application under the System/Preferences menu to add Avastgui to the Applications menu.

It seems to be working ok but as I'm only new at linux it would be great if someone more knowledgeable could confirm this is correct.

---

