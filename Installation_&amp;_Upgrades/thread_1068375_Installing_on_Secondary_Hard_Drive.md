---
title: "Installing on Secondary Hard Drive"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by crapple on 2009-02-12
I want to install Ubuntu on my secondary hard drive.  It is a slave drive.  I want to use windows boot manger as the boot loader.  The first hard drive has xp on it.  I do not want to do anything to that one.  I want to install ubuntu on the other one and then use windows boot manger to do all the booting stuff. Any ideas on how to do this?

Thanks

---

### Post by The Staucher on 2009-02-12
I am having my own issues, I am new to this just by a couple weeks, however...........

Just by gathering my thought as I have been reading that the windows boot manager does not like to share and that installing Ubuntu with the Grub boot manager auto detects other operating systems. So why wouldn't you want to use grub?
-Nebi1Kenobi

---

### Post by crapple on 2009-02-13
I have windows installed on the master drive and I got a new hard drive I want to put ubuntu on how do I do this.  My computer will automatically boot to windows because it is the master drive.

---

### Post by Pumalite on 2009-02-13
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Taemojitsu on 2009-02-13
If you use EBCD from [neosmart.net](http://neosmart.net/wiki/display/EBCD/), you can set up the Vista bootloader to let you boot into Ubuntu.

You can install the Vista bootloader onto XP, you just need to download the bootmanager file and put it in the right place, then use EBCD to point to it in the MBR.

You can even use EBCD to point to a Grub location, which can let you boot back to your Windows Vista bootloader, which you can instruct to load ('chainload') Grub, which you can then tell to load Ubuntu.. o.0


If you do decide to install Grub, it will go onto the MBR and the partition thing for your Windows installation will be unchanged (unless you have the Vista bootloader already, in which case Grub will steal the MBR from it). Grub looks at the different OS's available, and if you choose Windows then it loads Windows by following the instructions in the partition table of the Windows partition. No Grub files are saved onto the Windows partition when Grub is installed; all Grub files go in the /boot folder of your Ubuntu distribution, with the 'installation location' you select actually being for Grub Stage 1 which goes in the boot record

---

