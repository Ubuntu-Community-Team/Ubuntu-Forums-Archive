---
title: "NTLDR missing after runing the demo of Ubuntu"
date: 2008-07-18
forum: General Help
---

### Post by {=WaffleS=} on 2008-07-18
Well title says it all. I am running XP. I need help fixing this I know how to get around it but, it's getting annoying:(. And I can't run Live CD with this.

The Error Message:

NTLDR is Missing
Ctrl-Alt-Delet to restart


Thanks! :D

---

### Post by Kevbert on 2008-07-18
It looks like you've mucked up the Master Boot Record (MBR).  Best way to recover is to use your original XP CD.  Boot from this and run the program until you get the option to go into Recovery Mode. Do this so that you get to a DOS prompt. Now enter the following commands:
```
fixmbr
fixboot
```
NTLDR is a hidden file which is part of the MBR.
Once this is done you can remove the CD and reboot your PC.

---

### Post by {=WaffleS=} on 2008-07-18
> **Kevbert said:**
> It looks like you've mucked up the Master Boot Record (MBR).  Best way to recover is to use your original XP CD.  Boot from this and run the program until you get the option to go into Recovery Mode. Do this so that you get to a DOS prompt. Now enter the following commands:
```
fixmbr
fixboot
```
NTLDR is a hidden file which is part of the MBR.
Once this is done you can remove the CD and reboot your PC.

I don't have the Windows XP CD because it came with my computer when I bought it. I do have the recovery disks, one disk just has the OS on it would that work?

---

### Post by jimv on 2008-07-18
YEah, there should be a disk that says operating system or something like that.  It will have XP on it, and you need to use it to get into the recovery console.

Here's some instructions on getting into the recovery console, then you can run those two tools that the last guy mentioned:

[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

---

### Post by Kevbert on 2008-07-18
> **{=WaffleS=} said:**
> I don't have the Windows XP CD because it came with my computer when I bought it. I do have the recovery disks, one disk just has the OS on it would that work?
Be very careful as some recovery disks will only let you re-install the complete operating system and not recover just the Master Boot Record.  If you can boot from floppy disk it may be worth trying that as then you have the opportunity to backup any data that you may want to save.

---

### Post by Mgiacchetti on 2008-07-18
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)   check out fixmbr on that page, you will need a boot floppy...

---

