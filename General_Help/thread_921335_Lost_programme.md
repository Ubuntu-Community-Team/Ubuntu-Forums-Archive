---
title: "Lost programme"
date: 2008-09-16
forum: General Help
---

### Post by maravingian on 2008-09-16
Can anyone help?

I have installed AVAST ANTIVIRUS but have lost the program.  It does not show up on the Applications menu.  Every time i want to use it I have to search files for the directory, then each time have to input the license key.  Surely there must be a way of adding AVAST to the applications menu or an icon to the desktop to click on so you DONT have to input the license key EVERY single time???!!!!

Anyone, PLEASE HELP!!:lolflag:

---

### Post by tuxxy on 2008-09-16
Right clcik you menu and select edit menus, now add a new launcher for avast here

---

### Post by dualpretop on 2008-09-16
[http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb)

Terminal:

cd /usr/lib/avast4workstation/share/avast/desktop

sudo ./install-desktop-entries.sh install


Applications...Accessories...Avast

---

### Post by maravingian on 2008-09-18
Many Thanks for your help.  I have been able to install the AVAST Anti-virus programme from the Applications menu.  Now I only have to deal with why it isn`t scanning.

It gets to 950 files then an error scanning message appears.  It then says permission denied???

Just my luck I guess!!!:)

---

### Post by mb_webguy on 2008-09-18
You probably need to run Avast as root, especially if you're scanning outside of your home directory.  Right click on the menu as you previously did to edit the menus, locate the launcher for Avast, and add "gksu" to the beginning of the command.  So if the command is "/usr/bin/avast", change it to "gksu /usr/bin/avast".

---

