---
title: "Trying to install Grub only on SD card/USB disk"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Thetherumcompound on 2009-10-03
Hi
   I have been trying to do something that I guess is radical, install Ubuntu directly to a SD card.

The ideal way this would work is:

[LIST=1]
[*]Plug in a SD card/USB Memory drive to any computer I wish to use
[*]Boot up the computer and boot from the SD card/USB Stick
[*]Run Ubuntu directly from the SD card/USB stick with no changes to the host computer
[/LIST]
   I found out that ubuntu can be installed to practically anything from the pretty install GUI(Graphical user interface), and attempted to do so. I have an embedded SD card reader. I used the new beta for Ubuntu 9.10 and it installed completely with no errors were raised. When I tried to boot the SD card I installed it to(Sandisk 4Gb HC) it booted fine. But, when I tried to boot from my hard-disk I found that Ubuntu had replaced my hard-disk's bootloader with the one one my SD card. This raises a few problems like

[LIST]
[*]My hard-disk can no longer boot without the SD card.
[*]My SD card could only boot on my computer.
[/LIST]
I then installed Ubuntu 9.10 directly to my hard-disk and now I can boot without the SD card but, my SD card can still only boot on the computer I installed it on.
My question is:
Is there some way to I can install GRUB on an SD card so I can boot on other computers without being bound to one computer?

Any help will be greatly appreciated.

The Therum Compound

---

### Post by Thetherumcompound on 2009-10-04
I have been looking around on the forums and found a command that I thought would install grub the way I wanted. Unfortunately it returned an error...
```

**root@JPECKERT:/home/rob#** grub-install /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Invalid device `/dev/sdb1'.
Try ``grub-setup --help'' for more information.
**root@JPECKERT:/home/rob# **

```Is this because I have the new version of grub? Is there a similar command for the new version?

If it this helps, I am running off the file system that i am  trying to install grub to.

Thanks once again.

---

### Post by Thetherumcompound on 2009-10-04
I tried to use the above command to install grub from ubuntu 9.04 on my HD and the terminal returned...

```
root@JohnAdamPresperEckertJr:/home/rob# grub-install /dev/sdb1
/dev/sdb1 does not have any corresponding BIOS drive.
root@JohnAdamPresperEckertJr:/home/rob# 
```

Any help is welcome.

---

### Post by steveneddy on 2009-10-04
System --> Administration --> Create A USB Startup DISC

---

### Post by Thetherumcompound on 2009-10-04
I don't want to create a start-up disk as I want read-write abilities on the disk.I have already managed to install ubuntu 9.10 BETA on it the same way you install it to a hard disk. It runs just like it was on my HD except i can only boot it on the computer i made it on. I do, though,  	 	avenue before.

---

### Post by Thetherumcompound on 2009-10-04
What I really need is a terminal command or install instructions to install the new version of grub.

---

### Post by pmunly on 2009-11-12
I am attempting to do the same with 9.10 UNR... I am currently going through the installation process at this point, and I *think* I've done things so the bootloader will be installed onto my SD Card.  Here's what I did:

1. Boot up with my live image (this was on an SD card also - not the one I'm installing to)
2. Inserted SD Card to install to -> /dev/sde on my system
3. Ran the Disk Utility app in System.  Wiped my install SD Card and created an ext4 partition and a swap partition, made the ext4 partition bootable.
4. Just to be sure, I opened up gparted to verify everything on /dev/sde was correct & bootable
5. Ran the UNR install program - went through as usual until step 4 or 5 (I don't remember exactly; the one that allows you to choose which disk to install upon).  Two options were available - Erase entire disk (with a drop-down), and Custom.  I chose to Erase entire disk *AFTER* selecting /dev/sde - my SD Card.
6. Continued through the install process to step 7, the last step before installing.  After verifying all information displayed, I clicked on the Advanced button.. this brings up a window which asks which device to install the bootloader upon.  From here I verified that /dev/sde was selected and checked as "bootable." 

Currently the install is ongoing; once it's done I'll update this and let you know whether or not it worked as desired. :)

**** UPDATE ****

Everything works.  I'm able to boot off the SD Card (and am writing this from my new Ubuntu 9.10 UNR SD Card), my existing Windows partition was not effected & I'm able go boot into that as well.  Let me know if my above instructions are not clear.

---

### Post by Thetherumcompound on 2009-11-12
Thanks for your help!

---

### Post by Fdrock on 2009-11-12
Hey Guys, can this be done also with a 4gig usb drive?
That's exactly what i been looking to do

---

### Post by pmunly on 2009-11-13
Yep, I don't see why not.  The process should be basically the same, just be sure you know your thumbdrive's /dev/sd# after you plug it in.

---

### Post by Fdrock on 2009-11-14
How do i find that out?
Thanks for the help

---

