---
title: "Installing to an external HD"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by bchan009 on 2009-07-06
Hi guys,

Long story short, I need ubuntu fully bootable and independent off of an USB External HDD without installing ANYTHING on my laptop's internal drive.

I'm looking to install Ubuntu to a USB HDD so I can mess around with linux while leaving my Macbook Pro's internal drive untouched.  I'd like the USB HDD to be a full operating system that I can boot when I'm not using Windows or Mac OS X, which are already installed.

If possible, it'd be nice to have it so I can take it to other computers and boot from USB, so I'll have Linux wherever I go.

I've read that you could just make a LiveUSB, but that won't really save my data, so I can't use it like a portable PC.  I also read something about 'persistance', but from what I can tell it's still not the same as truly installing Ubuntu.

What is the best way to do this?  Searching has shown me that Ubuntu will try to install GRUB on my internal drive, and that the best way to get around this is to unplug my internal drive.  If I was on a desktop this wouldn't be a problem, but I need this laptop for work and am extremely loathe to open this baby up and have an accident.

I don't want GRUB on my internal HDD because then I'll have to have the USB HDD plugged in in order for my system to boot, and also because with Mac OS X 10.6 around the corner I fear whatever system I use to juggle partitions will be messed up if Boot Camp gets any upgrades/changes, etc.

---

### Post by howefield on 2009-07-06
During the install process, on the Ready to Install page, there is an Advanced button which lets you tell the installer where to put grub.

This should help you keep grub away from your internal drive. Although, I would want to make sure I knew how to restore the mac bootloader just in case ;)

---

### Post by earthpigg on 2009-07-06
download the .iso -> burn it to a cd -> boot from the cd with 'make no changes to my computer' selected -> go to system -> administration -> usb startub disc creator -> point it to the same iso you used to burn the cd -> carefully read the options during the process to ensure you make it persistent 

work?

---

### Post by loomsen on 2009-07-06
Just posted this...

[http://ubuntuforums.org/showthread.php?p=7568887#post7568887](http://ubuntuforums.org/showthread.php?p=7568887#post7568887)

---

### Post by Mighty_Joe on 2009-07-06
> **earthpigg said:**
> 
work?

No. According to the [Intel Mac FAQ]("http://ubuntuforums.org/showthread.php?t=1046568") you can't boot Ubuntu from an external drive. 

@bchan009, you should start with the above FAQ and have a gander at the [Mac forum]("http://ubuntuforums.org/forumdisplay.php?f=328")

---

### Post by loomsen on 2009-07-06
Alright, ignore me...

---

### Post by Alxl on 2009-07-20
I downloaded Portable Ubuntu Remix from   [http://sourceforge.net/](http://sourceforge.net/)   and am also using XP. 
And one does not need to reboot to get to the one or the other.
 I am new to Linux and do not understand how it was done but you can read about it, if still interested.
It can be installed on a USB stick too.
And it is persistent.
Let us know

---

