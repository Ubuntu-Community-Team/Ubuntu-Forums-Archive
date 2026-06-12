---
title: "Install windows through ubuntu"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by angeleyes on 2006-01-16
Ok got a question..
I like most of what ubuntu offers but my husband and kids like Windows better.
I want to know if there's anyway I can install my Windows Me using Ubuntu?I have XP on my computer,but somehow during the installation of Ubuntu I lost a important boot file so I can no ,onger boot my XP(I dont have a boot disk for it either)so I was going to use the ME disk I have.
I would appreciate an6 help you can give me in this matter.

---

### Post by Sef on 2006-01-16
Read this from Ubuntu - EasyLinux:

> How to add Windows entry into GRUB menu 
Read #General Notes 
Read #How to list partition tables 
e.g. Assumed that /dev/hda1 is the location of Windows partition 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
Append the following lines at the end of file 

titleMicrosoft Windows
root(hd0,0)
savedefault
makeactive
chainloader+1
Save the edited file

Link:  [http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu]("http://easylinux.info/wiki/Ubuntu#How_to_add_Windows_entry_into_GRUB_menu")

---

### Post by dcstar on 2006-01-16
[QUOTE=angeleyes]Ok got a question..
I like most of what ubuntu offers but my husband and kids like Windows better.
I want to know if there's anyway I can install my Windows Me using Ubuntu?I have XP on my computer,but somehow during the installation of Ubuntu I lost a important boot file so I can no ,onger boot my XP(I dont have a boot disk for it either)so I was going to use the ME disk I have.
I would appreciate an6 help you can give me in this matter.[/QUOTE]
If XP is still on your machine, it should appear in your Grub boot menu, or you should be able to add it back in:

[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

---

