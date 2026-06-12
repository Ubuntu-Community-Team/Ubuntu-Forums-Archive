---
title: "Problem with USB Install from the command line"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by RobMalcolm on 2009-01-22
Is there a way to kickstart the install from the command line

Background
I've bought a new HP 2133 mini laptop - this came with Suse 10, but the install failed first time with Grub Error 17.

Following the instructions on this forum ( big thanks ) I re-installed grub and set it to boot from (hd0,1) which was where the suse image ( i'd guessed) was. This failed again.

I was planning on installing ubuntu anyway
Spec
    * VIA C7®-M ULV Processor
    * 1.2 GHz, 128 KB L2 cache
    * Standard memory 1 x 1024MB DDR2
    * Chipset VN896NB and 8237S SB

Where I am so far
I managed to create a bootable USB stick from the ubuntu 810 iso file using UnetBootin
When I boot up the laptop using this drive it gives me the following 3 options

Default
/ubukern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
Help
/ubnkern initrd=/ubninit

oem=OEM install ( for manufacturers)

The default option looks like it starts ok, I get to the ubuntu screen with the loading bar, then the screen has blocks of colour scrolling, then goes blank. Stays blank until you re-boot.

The other 2 options fail with
Gave up waiting for root device.
ALERT! does not exist. Dropping to a shell

I am able to then mount the USB stick to root. 

Is there a way to kickstart the install from the command line

---

### Post by dabl on 2009-01-22
> **RobMalcolm said:**
> 

Following the instructions on this forum ( big thanks ) I re-installed grub 

You re-installed grub to the hard drive in the computer, or to the MBR of the USB stick?  The bootable USB sticks that I have made are with Grub installed on the USB stick, so it (the computer) never gets to the hard drive before booting starts.

---

### Post by RobMalcolm on 2009-01-22
It's on the Hard drive, as my initial problem was with Grub failing to work, so I re-installed it. How do I make the MBR on the usb stick ?

---

### Post by RobMalcolm on 2009-01-23
I managed to get this working

Useful link for this hardware here
[ubuntu-8-10 on hp-mininote]("http://sites.vanasdale.com/ubuntu-8-10-intrepid-ibex-on-hp-mini-note-kx870at/Home")

Turns out that there is an issue with the video drivers on this hardware. I followed the instructions but I had to use the Ubuntu 8.04 version as 8.10 still didn't work.

So steps are here
Download the Ubuntu LiveCD iso file you want.
Create a bootable USB stick
I did this using - [Unetbootin]("http://unetbootin.sourceforge.net/")
Boot from the USB, by hitting F9 at startup to show the boot devices menu.
When you get to the startup/install options you need to add xforcevesa into the command line. Pressing tab on my model allows you to see and edit the command, on other model F6 does the same.

After that the install goes normally

---

