---
title: "Only boots from flash drive"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by roger_e on 2009-11-12
I am replacing an XP system with Ubuntu..(no optical drive) so i used a flash drive and got it going, now it only boots from the flash drive...I reset the boot sequence and all of that.
 
I installed the "basic server" using Unetbootin(?)
 
What is th equickest way to get to ubuntu ver 8.04?....with no optical drive
 
I do have a laptop handy

---

### Post by mikewhatever on 2009-11-12
You may need to reinstall the GRUB boot loader, or check your boot order in the BIOS. The only version of Ubuntu you mentioned is 8.04, so I'm assuming, 8.04 it is.

[How to reinstall GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

As for 8.04 server, all server images are freely downloadable from releases.ubuntu.com. 
Direct link -> [http://releases.ubuntu.com/hardy/ubuntu-8.04.3-server-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.3-server-i386.iso)

---

### Post by Bunnybugs on 2009-11-12
Have you deleted the syslinux.cfg file that unetbootin created in the root of your flashdrive??

You'll need to rename the folder isolinux to syslinux, enter the new named syslinux folder, and find isolinux.cfg... rename this file to syslinux.cfg

Try to reboot now!

UNetBootIn is created to boot from USB, not from HDD...

Try this, and install Ubuntu fresh

EDIT: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) (This tells you what to do!)

---

### Post by roger_e on 2009-11-12
Slow down.....
 
[I]Have you deleted the syslinux.cfg file that unetbootin created in the root of your flashdrive??

You'll need to rename the folder isolinux to syslinux, enter the new named syslinux folder, and find isolinux.cfg... rename this file to syslinux.cfg
[/I]
Does this happen on the flash drive or the hard drive?
 
first you say delete syslinx.cfg then rename isolinux to syslinux?
 
Then reboot and reinstall?
 
correct?

---

### Post by Bunnybugs on 2009-11-12
> **roger_e said:**
> Slow down.....
 
[I]Have you deleted the syslinux.cfg file that unetbootin created in the root of your flashdrive??

You'll need to rename the folder isolinux to syslinux, enter the new named syslinux folder, and find isolinux.cfg... rename this file to syslinux.cfg
[/I]
Does this happen on the flash drive or the hard drive?
 
first you say delete syslinx.cfg then rename isolinux to syslinux?
 
Then reboot and reinstall?
 
correct?


On the root of the flashdrive, not teh hard drive...

Unetbootin doesn't really work with Ubuntu, had the same trouble with the UNet version of syslinux

All of this is on the flashdrive... just make a new, clean install of Ubuntu

---

