---
title: "There has to be an easier way.....  A dual boot question"
date: 2008-08-10
forum: General Help
---

### Post by DeadlyOats on 2008-08-10
I want to dual boot Win XP on my Ubuntu Laptop.  The trouble is, my laptop has no floppy.  I read an [article]("http://tarunreflex.wordpress.com/2008/06/30/install-windows-xp-on-sata-without-a-floppy-f6/") on how to use Nlite to install Win XP onto a floppy-less system.

First, is there an easier way?  And next, is there an easier way?

---

### Post by damoxc on 2008-08-10
Can't you just install Windows XP via CD, then use the Ubuntu CD to reinstall grub to the MBR, then run update-grub in Ubuntu and it should pick up your Windows XP install.

---

### Post by jerome1232 on 2008-08-10
The only reason you would need a floppy is if you have sata controllers that XP doesn't recognize, and even then your BIOS usually lets you set your sata controller to an IDE compatibility mode.

---

### Post by issih on 2008-08-10
I doubt there is an easier way...installing windows is a pain. given xp's venerable age I doubt it will pick up a flash drive instead of the floppy in the installer, so if your sata controller is not already included in the xp install cd then you are going to have to use nlite, or find a way to temporarily jack a floppy drive into your laptop :)

---

### Post by DeadlyOats on 2008-08-10
It figures....  :(

Windows!   ](*,)

---

### Post by Mgiacchetti on 2008-08-10
actually i have found that nLite isnt that hard of a program to use, its just the pain of burning another disk.

---

### Post by DeadlyOats on 2008-08-11
Is there a Linux version of nLite for Ubuntu?  I don't have access to a Windows machine.

---

### Post by jerome1232 on 2008-08-11
Do it in a VM, that's what I do at least.

---

### Post by djrobthaman on 2008-08-11
Not everybody needs floppies to install windows.  But you could try and defrag your drive a few times, then use the partition resize tool on the ubuntu livecd to make some space for ubuntu.

---

