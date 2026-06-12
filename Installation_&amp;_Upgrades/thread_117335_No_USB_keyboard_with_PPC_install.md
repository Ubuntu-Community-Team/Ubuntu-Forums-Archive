---
title: "No USB keyboard with PPC install?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by georage on 2006-01-14
The PPC-version of the 5.10 Live CD boots, but their doesn't seem to be USB keyboard support because I can't type anything when I get to the boot prompt.

Machine specs: iMac G3, 333mhz, 96megs, tray loader.

I get the same error with Debian 3.1 installer and Gentoo's latest "live" CD. I have burned several disks and all halt after the yaboot message.

Is there a way to make an ISO that automatically kicks off an Ubuntu default install after a few seconds? That would perhaps load up USB keyboard support.

This is my first PPC install of Linux. It has not been pretty.

---

### Post by linear on 2006-01-14
No, a USB keyboard should work. Is it Apple or third party? Also, is it plugged into a hub or directly into the iMac? (If into hub, try direct.)

---

### Post by georage on 2006-01-15
Here's how I installed Ubuntu on an iMac 333, 96megs.

At first, I tried to install Ubuntu over the exisiting System 9.1 on the 6 gig hard drive, but, not matter what I tried, the computer would always boot 9.1, pressing "C" or any other combination of keys did nothing. The caps lock light would always come on and stay on.

While still using the old hard drive, I download Micromat's TechTool Lite and zapped the PRAM. I could not zap the PRAM using keyboard commands. 

I removed the 6 gig hard drive and replaced it with a 20 gig ATA drive, set to master.

I depressed the "programmers button" near the Ethernet connection and hit restart and waited for the long tone.

Using a System 9.1 boot disk, I partitioned the drive into 2 partitions, one 6gig Mac OS partition and another unallocated partition. The "C" button still did not work, but I waited and put the CD in the tray a couple of times and it finally booted from the CD. 

I did a "clean install" on the 6 gig partition. This is important, an earlier attempt using a regular install did not boot, but a clean install did. 

I rebooted into the new 9.1 install.

I noticed the Caps Lock light never came on!

I rebooted with an Ubuntu CD ... and it was recognized AND I could hit return! The keyboard finally worked!

I formatted the whole drive and installed Ubuntu. 

THE END

---

### Post by sarcasticfrench on 2006-04-11
I've got the EXACT same problem. I've tried both Ubuntu, Kubuntu, and Gentoo, and like yours all of them halted at the boot loader screen. Maybe it's the boot loader? I don't have another hard drive sitting around, so I can't try the whole clean install of os 9 onto a seperate partition thing. I did get Ubuntu to work on my iBook g3 300 mhz, so maybe its something about the USB keyboard? I might try to get a new one, maybe that will work.


EDIT: It turns out my DVD/CD ROM drive just didn't like the cheap-o GQ cd-r's you get at Fry's, and when I tried it with a different brand of CD R it worked just fine.

---

### Post by rpm1200 on 2006-04-26
I have the same problem.  I tried to install Breezy on my iMac rev B (bondi, tray-load 233) without using a cd-rom because the iMac's cd-rom drive was dead.  I connected two hard drives to the hard drive IDE connector and tried to install Breezy from the primary to the secondary drive.  The install appeared to run fine but when I got to the end, shut down the PC, disconnected the drive with the install disk files and made the other drive the master, it would not boot (the primary boot loader would come up, then the secondary one would fail with a flashing folder for about 10 seconds, then the primary boot loader would come up again - it would loop forever).  Also, it would not respond to keyboard commands anymore like command-option-O-F or command-option P-R.  I have another hard drive loaded with Mac OS 9.1 - if I install that, I can boot into Mac OS just fine - the keyboard works once I'm in Mac OS.  I've tried installing Mac OS 9 on one of my extra hard drives and I did succeed in restoring pre-boot keyboard functionality once - I just can't figure out the exact steps that worked for me.  I more or less followed the steps above and they did not work for me.  
I can get Open Firmware 3 to come up if I hold down the programmer button during the startup chime - the keyboard just does not work at that point.  I have a non-Mac USB keyboard.  Usually I leave it plugged directly in but I have used it with a Belkin powered 4-port hub.  The hub seems to have no positive or negative effect, and it gives me an indication of when the keyboard is enabled.  When everything is working normally the hub shows the keyboard as active shortly after the system chime, but when the system is in the bad state the keyboard goes active shortly after the "happy mac" appears.  
Unfortunately I can't try an ADB keyboard because there's no ADB port on a rev B iMac.  I also do not have access to a Mac USB keyboard but I don't think it would make any difference - my HP USB keyboard worked fine earlier in Open Firmware (command-option-O-F and command-option-P-R did work at one point, using the windows key for command and the alt key for option) and it always works fine in Mac OS 9.
If I ever figure out how to restore pre-boot keyboard functionality every time I will post it here!

---

### Post by rpm1200 on 2006-04-27
Hmmm... it's working fine now and I STILL don't know exactly how I did it!  I have a suspicion that I just did not wait long enough - after installing Mac OS 9 again on my extra drive then letting the iMac sit all day, it came up with full keyboard functionality and I was able to get back into Open Firmware.
Also have a working CD-ROM now... I scavenged a Teac CD-224E from an old Compaq laptop.  The drive does not have a master/slave/cable select switch, it is always in cable select mode, which is a problem because the iMac leaves the CSEL pin open - this makes the drive behave as a slave.  I solved the problem by making a solder bridge between pin 45 (ground) and pin 47 (CSEL) on the connector that plugs into the CD-ROM drive (not the connector that plugs into the iMac MLB!).  Got that idea from this page: [http://www.xlr8yourmac.com/PB_G3/oem_combo_drives/notebook_combo_drive.html]("http://www.xlr8yourmac.com/PB_G3/oem_combo_drives/notebook_combo_drive.html")
Installing Breezy now using the CD-ROM... hope it works this time around...

---

