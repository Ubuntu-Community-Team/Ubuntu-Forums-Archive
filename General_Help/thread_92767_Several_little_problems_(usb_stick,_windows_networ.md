---
title: "Several little problems (usb stick, windows network, windows partition)"
date: 2005-11-20
forum: General Help
---

### Post by UeB on 2005-11-20
1. windows patition
I want to have writing permission on the windows partion (formated with fat32 and mounted as hda2)
what i tried:
change the rights in gnome (right click on the drive symbol on the desktop then on properties etc..)
but not possible as normal user.
created changed the root password, loged in gome as root (had to change some option that this is possible) tried the same but when i check the write perimission it is instantly automaticialy unchecked again.

2. windows network
till some days ago it was no problem to access the my windows (windows 2000) pc sitting in the same LAN and read or write files. But when i try to access the windows network with ubuntu now it a login window apears and asked me login domain and passwort athough this was not nessesary before and i didnt change anything speacially no passwort is set for the windows network.

3.
the easiest qustion at last. when i plug in an usb stick it apears instantly on the desktop and i can use the filemanager to access the data on it. But where can i find the files on the usb device in the command line? every part of the linux filessystem exept the my "home" folder is a big black box for me.

---

### Post by aysiu on 2005-11-20
[QUOTE=UeB]1. windows patition
I want to have writing permission on the windows partion (formated with fat32 and mounted as hda2)
what i tried:
change the rights in gnome (right click on the drive symbol on the desktop then on properties etc..)
but not possible as normal user.
created changed the root password, loged in gome as root (had to change some option that this is possible) tried the same but when i check the write perimission it is instantly automaticialy unchecked again.[/quote] Do this instead: [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

> 
2. windows network
till some days ago it was no problem to access the my windows (windows 2000) pc sitting in the same LAN and read or write files. But when i try to access the windows network with ubuntu now it a login window apears and asked me login domain and passwort athough this was not nessesary before and i didnt change anything speacially no passwort is set for the windows network. Can you post a screenshot of what that dialogue looks like? When it pops up, press Alt-Prt Scrn and then upload the file to your post ("manage attachments" below the "submit post" button).

> 
3.
the easiest qustion at last. when i plug in an usb stick it apears instantly on the desktop and i can use the filemanager to access the data on it. But where can i find the files on the usb device in the command line? every part of the linux filessystem exept the my "home" folder is a big black box for me. Type ```
df -h
``` in a terminal. That will tell you where it's mounted.

---

