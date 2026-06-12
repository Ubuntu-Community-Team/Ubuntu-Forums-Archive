---
title: "I need help...I installed Ubuntu and now I cant access my XP"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by angeleyes on 2006-01-09
I am new to Ubuntu 5.0 . when I was done installing it and tried to choose to run my XP in the OS options box I got this error:
the <Windows root>\system32\hal.dll is missing or currupt.
Is there anyway to fix this?so I can run my XP again without having to use the System Recovery for Windows?
I have alot of pictures and such on my XP that I can see when I use the disks option and look in my partition that holds Windows XP and I dont want to lose them.
Is there anyway to burn to a CDROM?I tried but I all it said was data disk not image--it alsom called them archive files.
Please I would appreciat any help given.

---

### Post by Glass Casket on 2006-01-09
Maybe try going in XP with safe mode on to back up your things.

---

### Post by angeleyes on 2006-01-09
I cant even get into safe mode in windows --I get the message as soon as I try and boot the program

---

### Post by nickj6282 on 2006-01-09
You can try copying the hal.dll from your Windows CD back to the System32 directory using a Knoppix CD with Captive-NTFS or something else that will let you read from the CD-ROM and write to the Windows partition. The file is in the i386 directory on the disk and will need to be renamed from hal.dl_ to hal.dll.

HTH
-Nick

---

### Post by aysiu on 2006-01-09
[QUOTE=angeleyes]
I have alot of pictures and such on my XP that I can see when I use the disks option and look in my partition that holds Windows XP and I dont want to lose them.
Is there anyway to burn to a CDROM?I tried but I all it said was data disk not image--it alsom called them archive files.[/QUOTE] Sure. See the fourth link of my sig. Then, ```
sudo apt-get install k3b
k3b
```

---

### Post by angeleyes on 2006-01-09
ok now Im gonna sound stupid here (,I just installed it )so..how do I open a terminal?

---

### Post by nickj6282 on 2006-01-09
In Gnome:

Applications menu --> Accessories --> Terminal

Should be similar in KDE. In fact, I think KDE has a terminal icon next to the applications menu.

-Nick

---

### Post by angeleyes on 2006-01-09
I m having trouble I go to Computer and click on the hda icon and tells me I dont have permission to view it---what do I do now?

---

