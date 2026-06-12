---
title: "Can't get Ubuntu installed with XP on nVidia RAID 1"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Grendelmon on 2008-12-20
Hello all,

I've been banging my head with this problem for quite some time and I'm about to give up.  I've searched high and low and can't seem to figure out if either 1) I'm doing something wrong or 2) this just isn't possible (or I'm making this harder than it really should be).

I built a gaming PC about two years ago with a Core 2 Duo, ASUS SLI motherboard, dual nVidia cards, and dual 80gb SATA hard drives running Windows XP Pro 64-bit in RAID 1 (striped).  I used RAID so that my gaming maps would load faster (Battlefield, COD, etc.)  It worked great (although I've had my share of Windows problems) but recently dove into using Linux as my OS of choice (I used to be a big Mac head, and then got an EEE using Xubuntu).  So instead of fighting with my RAID to get Linux running on a separate partition, I thought it would be simpler if I just dropped another SATA drive to dedicate for Ubuntu.  So, to cut to the chase, here's my current hardware:

ASUS P5N32-SLI Delux motherboard
Intel Core 2 Duo 6400 (1.86gz)
3gb 667mhz RAM
(2) EVGA nVidia 9600GT pci-x video cards SLI bridged
(2) 80gb Seagate SATA drives RAID 1 striped (XP 64-bit Pro installed)
(1) 320gb WD SATA drive

My headache is GRUB.  The problem I ran into was that the dual 80gb Seagate drives were using interfaces 0 and 1 out of the 8 SATA spots on the motherboard.  I dropped the WD drive and it was using interface 2 (the third).  When I installed Ubuntu, it was successful until it got to rebooting and GRUB started reporting "Error 21."  I booted from the LiveCD, tried to repair GRUB by performing the "find /boot/grub/stage1" , etc.  GRUB would find the device (something hd2,2), and root and setup were successful, until I would reboot again and still get "Error 21."

I couldn't recover my Windows XP at that point.  Booting off the XP disc and performing a recover with FIXBOOT and FIXMBR said it worked but when I restarted the BIOS complained there was no valid system disk.  I'm thinking it had something to do with using the nVidia RAID drivers and the recover really didn't fix anything.

Ugh.  I went into my BIOS, changed the boot order of the hard disks so the primary was my WD with Ubuntu.  Booted off LiveCD and tried to repair GRUB again.  Rebooted and GRUB still gave errors (17, 21, 22, I honestly don't remember).

So I popped open the box and switch the SATA interfaces around.  I stuck the WD Ubuntu drive in #0, and my RAID drives in #1 and #2.  I switched the BIOS again to make sure the WD was primary boot.  Reinstalled Ubuntu.  Same problem.  Then my process gets fuzzy because I started trying so many different things.  I can't exactly recall everything that I did now.  So I eventually wiped the RAID and reinstalled XP.  So XP boots now, Ubuntu is still on the WD but I don't have GRUB installed.  So I'm not really sure what the problem is.

Can someone suggest a way to configure my hardware to make this easier, or is this just a bad idea?  I appreciate any suggestions or tips.

Grendelmon


**EDIT**
I am using RAID 0, striped.  Also I've tried Ubuntu/Kubuntu 7.10 and 8.10

---

### Post by Grendelmon on 2008-12-25
Well, it's pretty quiet out there.

Apparently I'm not the only one who can't get this to work:

[http://ubuntuforums.org/showthread.php?t=347543]("http://ubuntuforums.org/showthread.php?t=347543")

I think that I'm just going to give up on this.  Any help would be appreciated.


:confused:

---

### Post by seubill on 2008-12-25
What version of Ubuntu are you trying to use? 8.10 desktop does not currently support software RAID arrays. I have read some discussion about the next Wubi revision being planned to do this, if you don't mind installing Ubuntu inside of Windoze as an application. Ubuntu Server will support hardware RAID controllers, but often requires BIOS revision/controller driver upgrades. Not much help, I know. Experienced the same problem you are having and I finally went with Fedora 10.

Just a note, on a 2 hard drive software RAID array, Level 0 is stripping, Level 1 is mirroring.

---

### Post by cashmoney on 2008-12-26
> **seubill said:**
> What version of Ubuntu are you trying to use? 8.10 desktop does not currently support software RAID arrays. I have read some discussion about the next Wubi revision being planned to do this, if you don't mind installing Ubuntu inside of Windoze as an application. Ubuntu Server will support hardware RAID controllers, but often requires BIOS revision/controller driver upgrades. Not much help, I know. Experienced the same problem you are having and I finally went with Fedora 10.

Just a note, on a 2 hard drive software RAID array, Level 0 is stripping, Level 1 is mirroring.

Not supported but it works.  I am currently typing this on my fresh install 64bit 8.10 with Fake Raid.   Follow this guide on install [http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid](http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid)

When it gets to the cli partitioning part I was able to do it in gparted.  But it worked for me.  Good luck man I'll subscribe and if you have anymore issues I'll try to help you through it. Now if I can figure out how to get my nvidia cards working I'll be set.

Nate

---

### Post by Grendelmon on 2008-12-26
> **seubill said:**
> What version of Ubuntu are you trying to use? 8.10 desktop does not currently support software RAID arrays. I have read some discussion about the next Wubi revision being planned to do this, if you don't mind installing Ubuntu inside of Windoze as an application. Ubuntu Server will support hardware RAID controllers, but often requires BIOS revision/controller driver upgrades. Not much help, I know. Experienced the same problem you are having and I finally went with Fedora 10.

Just a note, on a 2 hard drive software RAID array, Level 0 is stripping, Level 1 is mirroring.

Thanks for the correction and suggestion.

---

### Post by Grendelmon on 2008-12-26
> **cashmoney said:**
> Not supported but it works.  I am currently typing this on my fresh install 64bit 8.10 with Fake Raid.   Follow this guide on install [http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid](http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid)

When it gets to the cli partitioning part I was able to do it in gparted.  But it worked for me.  Good luck man I'll subscribe and if you have anymore issues I'll try to help you through it. Now if I can figure out how to get my nvidia cards working I'll be set.

Nate

Thanks for the link.  I finally gave up and destroyed the RAID, ended up putting Ubuntu 8.04 on one of the 80gb drives, and I'm planning on putting XP on the 320gb drive.  If I have time I might try to re-create the RAID array for XP and start over, maybe this weekend.  I appreciate the info.

---

