---
title: "ubuntu and xp"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by haze210 on 2005-12-06
i replaced windows with ubuntu. now i want windows back but i want to make it a duel boot pc. how do i uninstall ubunto and reinstall it along with xp. i want to get to know ubunto better but i need windows xp back so other people can use my pc. can someone please help.

---

### Post by giloth on 2005-12-06
To reinstall XP you just have to boot the XP CD when you start your computer. After XP is installed, boot from the Ubuntu CD and have it split the partition into several for the Ubuntu OS. (Not sure about Ubuntu, but most distros have automatic options for this). When you boot up, select the OS you want and go! 

Hope this helps!

---

### Post by haze210 on 2005-12-06
i popped in a xp cd restarted  the pc and nothing happened.

---

### Post by giloth on 2005-12-06
Sounds like you need to go into your BIOS and have your CD drive be a boot device BEFORE the hard drive.

Enter your BIOS when you start your computer by pressing F2, DEL, or whatever the command is for your system. (Most of the time it'll tell you what to press to enter setup).

Find the boot priority and set it so that the first device is your floppy, second is your CD Drive and third is your hard drive.

Now after you save your settings and have your XP cd in the drive, it should boot from it.

---

### Post by haze210 on 2005-12-06
my cd drive is set as the first then floppy then hard drive. nothing happened.

---

### Post by ericvmazzone on 2005-12-06
I have to do this everytime I want to reinstall XP on my AlienJUNK Laptop to be able to boot off the XP disk.  I have to remove all of my RAM from my box for a few min.  Make sure all power is off and removed from your box before you try this.

---

### Post by haze210 on 2005-12-06
would it help if i said i had 15 gb of free space i didnt partition the whole hd.

---

### Post by Arktis on 2005-12-06
Boot from a windows 98 floppy boot disk.  You can get one off the internet easily by googling but just make sure it has cdrom support and smartdrive.  Once your computer is booted from the floppy, issue the command:
```
smartdrv
```
That will load smartdrive, which will ensure that you have fast disk access.  Without it, the installation will CRAWL.
Next, change to the cdrom drive and do:
```
cd i386
winnt
```
This will allow you to do a windows xp installation, but only using fat32.  You can convert the partition later if you really want ntfs.

---

### Post by haze210 on 2005-12-07
i downloaded a boot disk and when i reboot the computer i say the disk is not bootable or some thing like that

---

