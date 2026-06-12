---
title: "Running Ubuntu from a USB"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by yorkshireflatcap on 2009-11-04
All,

After much hair pulling and ](*,)I've managed to put Ubuntu 9.10 on my 4gb memory stick.  I know that I can boot up Ubuntu from the USB, because I'm using it now.  

I've created a user with a password, how do I get this account to be the default account upon startup from the usb?  It seems that I have to create a new user account every time I boot from USB.

Secondly, I have a broken version of Ubuntu 9.10 installed on my laptop - how do I get rid of previous OS that are residing on my laptop and also redefine partitions.

Oh, btw, I need to be able to keep my original /home/user directory as it has 32Gb of data... Any ideas?

Since being able to figure out how to boot from USB, I don't know why I didn't think of doing this earlier!! :D

---

### Post by bruno9779 on 2009-11-04
I can't answer your first question.

For waht concerns getting rid of other OS and reorganizing partitions, Live CD/USB is the best way:

- Log in a live session
- Go to Gparted (aka partition editor)
- happy resizing!

---

### Post by Bunnybugs on 2009-11-04
Use NetBootIn...

Make a liveUSB stick...

You can download ubuntu in this program, or you use a downloaded .ISO file... (Watch out, it must be Desktop-version, not alternate!)

Make the disc

Delete the SYSLINUX.CFG file on your USB root, Rename the folder ISOLINUX to SYSLINUX, go into the SYSLINUX-folder, rename ISOLINUX.CFG to SYSLINUX.CFG

Reboot your PC, go into bios, and set your USB-device as the first booting-device,

From here, you can boot, or you can set up a live version... it's not possible to use your own Username/Password...

---

### Post by yorkshireflatcap on 2009-11-04
> **bruno9779 said:**
> I can't answer your first question.

For waht concerns getting rid of other OS and reorganizing partitions, Live CD/USB is the best way:

- Log in a live session
- Go to Gparted (aka partition editor)
- happy resizing!


I hope this isn't as silly as it sounds, but I have 32Gb of data - files, vids and family pics that I want to keep, or transfer over.  How do I go about partitioning my HDD without losing my aforementioned files?

Many thanks.

Yorki

---

### Post by Mighty_Joe on 2009-11-04
> **yorkshireflatcap said:**
> I've created a user with a password, how do I get this account to be the default account upon startup from the usb?  It seems that I have to create a new user account every time I boot from USB.


How did you put Ubuntu on your flash drive?  It sounds like you did a Live CD style install but didn't opt for a persistent partition or file to save your changes.

---

### Post by jdeca57 on 2009-11-04
> **yorkshireflatcap said:**
> I hope this isn't as silly as it sounds, but I have 32Gb of data - files, vids and family pics that I want to keep, or transfer over.  How do I go about partitioning my HDD without losing my aforementioned files?

Many thanks.

Yorki

Backup to an external usb hard drive? Actually, I installed 9.10 on external drive (with plenty room for those pics). Ok, new drives with 1 or 2 TB remain expensive, just look at the past generation of drives. 320 GB is a lot of space...

---

### Post by FiveSidedPoly on 2009-11-04
> **Mighty_Joe said:**
> How did you put Ubuntu on your flash drive? It sounds like you did a Live CD style install but didn't opt for a persistent partition or file to save your changes.
 
+1
 
I bet you installed a "Live USB", which is the same as your Live CD. 
 
What you can do now if you have another usb drive (2nd), just boot up with the Live USB you have now, plug the other usb drive (2nd) in and do use the "Install" icon on your desktop to install it on the 2nd usb drive.
 
You could also use the Live CD to install a fresh copy of Ubuntu onto the usb drive that you have as a Live USB now.
 
I've recently installed Karmic on 8 usb drives for friends using both methods.

---

