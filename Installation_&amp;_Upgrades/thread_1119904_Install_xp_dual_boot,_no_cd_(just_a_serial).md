---
title: "Install xp dual boot, no cd (just a serial)"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by hozzy on 2009-04-08
My computer came with xp installed, and I have a serial number pasted to the bottom of my eeepc. I wanted to try linux, got really excited, clicked too fast, didn't read enough and failed (lost windows and couldn't boot into Linux). That was a while ago, and after downloading ubuntu and then ebuntu, I now finally have a working computer.

I want to have xp back on this machine and I know there is a way to do it, I have read a number of tutorials, my problem is that I don't have a dvd-rom drive, but I do have the Internet and I do have a legit and legal xp serial number. If I get an xp iso, how can I put that on a 8gb usb drive to boot and install windows. It has to be done in ebuntu.

Any help would be great appreciated. Thanks

---

### Post by Mark Phelps on 2009-04-08
Before you attempt anything, you would need to confirm that your PC can boot from a USB drive -- not all can.  Look into your BOOT options in your BIOS setup and confirm that there is an option to boot from USB or external device.

I say that because, as far as I know, you can't install XP from inside Ubuntu.  You'd have to be able to run the appropriate setup .exe file, and you can't do that in Ubuntu.  You'd have to be able to boot from the USB stick to install XP.

Once you know that you CAN boot from USB, you will have to make the USB bootable.  I don't know the details for doing that.  You will have to search the forums for that.

Before you install XP, though, you will have to repartition your drive to make room for it.  XP wants to be the first partition on the drive, so you will have to use the Gnome Partition Editor, or the GParted LiveCD (which you can get from distrowatch.com) to resize and move your Ubuntu partitions to the right to create unallocated space to the left.

When you install XP, it will overwrite the MBR, effectively wiping out the ability to boot into Ubuntu.  So, you will then have to reinstall GRUB from a LiveCD to get Ubuntu boot back.

---

### Post by hozzy on 2009-04-08
My computer can boot from USB. I know that I have to repartition the drive and I know I have to re-install grub. What I don't know is how to make a bootable usb drive that can boot and install windows, I have tried to put the recovery dvd on a 8gb usb drive but ran into problems (I think because it was wasn't formatted fat16).

Does anyone know how to make a bootable usb drive to install xp. I can only use linux tools to do this (as that is  all I have). Thanks

---

### Post by lisati on 2009-04-08
Suggestion: keep an eye out for a "recovery" partition, clobbering it when you don't have a backup can be a pain if you ever need to go back to XP (for whatever reason). I'm not familiar with what comes preloaded on the eee: if you're lucky, there'll be a program to make a backup of the recovery partition.

---

