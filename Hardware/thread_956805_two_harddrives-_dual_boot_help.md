---
title: "two harddrives- dual boot help"
date: 2008-10-23
forum: Hardware
---

### Post by eventualchaos on 2008-10-23
So I had two computers, one running xp, and one running ubuntu. The one with xp is pretty old and is now pooched, so I decided to put some it's harddrive into my ubuntu system. now I'm completely new to dual booting and I'm not sure how to set the jumpers and such. I'm wondering what would be the easiest way to dual boot between the two?

---

### Post by jhenager on 2008-10-23
I would leave the jumper on the Ubuntu system like it is. It should be jumpered to be Master. The XP drive is also probably jumpered Master. This should be made Slave.
Then install the XP drive and look at this page for help on how to modify GRUB to allow you to choose at bootup. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dabl on 2008-10-23
Hmmmm -- glutton for punishment, eh?  :lolflag:


Prolly you want to jumper both drives "cable select" or "CS" -- that lets BIOS control which one is first.


Depending on your personal view of "easiest", you're looking at a short list of real tricky issues:

1. Win XP, at the time of installation, is configured very "hardware-specific" -- there's little chance that the XP OS on that hard drive will run correctly on another computer, unless it is a dead-ringer twin of the hardware that the hard drive came out of.  So I think you get to perform the Windows installation ritual.

2. Both hard drives already have the MBR written, to boot _just_ that hard drive.  You're going to have to become a bit of a "Grub Maestro" and use several of the grub commands, including "geometry" and "grub-update", to re-write whichever MBR is going to control booting.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


I think what you want to do is, after hooking up the second hard drive, and setting the sequence in BIOS the way you want it, is FIRST to install Win XP on that drive, and SECOND twiddle Grub, as per Herman's guidance, to overwrite the MBR of the hdd that has Win XP on it to include booting *buntu, so in the end you have a Grub boot menu that offers *buntu and Win XP.

---

### Post by eventualchaos on 2008-10-23
okay so I set the ubuntu harddrive to master and xp's to slave. when I turn on my computer i hit f8 for boot options and select the xp if i want to boot with it. it works perfectly except in xp I can't access the harddrive with ubuntu. is there any way to transfer files to xp directly from the ubuntu hd?

---

