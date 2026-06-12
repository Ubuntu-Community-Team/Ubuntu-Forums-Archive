---
title: "Smartbootmgr. not able to find CD drive"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by oljeogvann on 2005-08-29
Hi
I am new to ubuntu 5.04. I have an old laptop that can't boot from CD.
I have tried to boot from a floppy using smartbootmgr. 3.7.1 (The one on the ubuntu cd). It gives me a disk error when i try to boot the CD.
I have also tried to boot from floppy with syslinux boot. It doesn't help either.

But with the floppy syslinux boot diskette, i am able to find the cd device and mount it up. But HOW do i start the installation process from here?????
PLEASE HELP me. I have tried searching this forum without success.

---

### Post by tonysathre on 2005-08-29
did you try flashing your BIOS to upgrade it

---

### Post by oljeogvann on 2005-08-30
Yes
It's an old dell latitude XPi ( 1998 ). I have tried different BIOS upgrades, but none gives me the ability to to boot from cd rom.  :?

---

### Post by fparri on 2005-08-30
Maybe you can find help heer:
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by oljeogvann on 2005-08-31
Thank you very much fparri.
Your link sent me in the right direction.
Loadlin saved my day. The installation is running from the CD. :smile:

---

### Post by cas194 on 2005-08-31
I'm not sure if this is the same problem, or slightly different.....

I have an old machine which won't boot from CD which is currently running Caldera OpenLinux 2.2. I created two boot disks, one with rawwritewin and then another on the Caldera system. Neither offers CD-ROM as a boot option. I'm able to mount the Ubuntu CD and explore it, (I  created the second boot disk by retrieving the image from the install directory using dd) but SBM persists in ignoring the CD drive. 

Any more ideas, or am I going to have to go back to DOS/WIN and proceed from there with loadlin? I'd rather not......

---

