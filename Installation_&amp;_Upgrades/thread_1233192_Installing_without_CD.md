---
title: "Installing without CD"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by J_Sas on 2009-08-06
This is my first attempt at installing a Linux installation.

I followed the steps listed on another Thread to install without a CD.  Downloaded 9.04 for my AMD64 machine (ubuntu-9.04-desktop-amd64 (1).iso), have tried the steps to create a boot.ini line to grub4dos, have tried using unetbootin, both onto my other partition I created and onto a USB drive, still unable to install.  Any suggestions?

Jeff

---

### Post by running_rabbit07 on 2009-08-06
Try [Unetbootin]("http://unetbootin.sourceforge.net/"). It is a program that downloads everything you need to get started and then it will tell you to restart to begin the install. You have to select to download to your hard drive.

---

### Post by J_Sas on 2009-08-06
I did use unetbootin, as stated in my first post, however, I am trying to install to drive E: which is my second partition on the drive.  I selected USB drive, and the checkbox for "Show all drives" then selected drive E:, rebooted, and still got error messages. 

I just tried updating my vmlinuz and initrd.gz files from the ubuntu download just now and took down the error messages I got:

"marking TSC unstable due to TSC halts in idle

Gave up waiting for root device...

Alert! /dev/rd/o does not exist. Dropping to shell!"

Any advice?

---

### Post by running_rabbit07 on 2009-08-06
> **J_Sas said:**
> I did use unetbootin, as stated in my first post, however, I am trying to install to drive E: which is my second partition on the drive.  I selected USB drive, and the checkbox for "Show all drives" then selected drive E:, rebooted, and still got error messages. 

I just tried updating my vmlinuz and initrd.gz files from the ubuntu download just now and took down the error messages I got:

"marking TSC unstable due to TSC halts in idle

Gave up waiting for root device...

Alert! /dev/rd/o does not exist. Dropping to shell!"

Any advice?

To get it to boot from the USB device you have to set BIOS to look in the USB drive. If you tell it to download to hard drive then reboot it will start the install and after answering a few questions it will take you to the partitioner where you will be able to install in the "E" partition.

---

### Post by J_Sas on 2009-08-09
Finally resorted to just booting from CD.  Was trying to save a disc.  Thanks for your help!

Now I have a new question, which is in the Networking/Laptop area.

Thanks!
Jeff

---

