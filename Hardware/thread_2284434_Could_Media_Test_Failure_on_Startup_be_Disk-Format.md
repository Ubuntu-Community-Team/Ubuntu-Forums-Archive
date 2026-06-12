---
title: "Could Media Test Failure on Startup be Disk-Format related?"
date: 2015-06-29
forum: Hardware
---

### Post by barbarianeggplant on 2015-06-29
I maintain a group of dell e6410 laptops at my school. Basically all of them run win 7 pro, but I ended up with one running Trusty (as I do on my home computer) through the following circumstance:
-Upgraded a different laptop running XP to Ubuntu.
-DC plug port turns up broken and computer goes on the parts pile.
-Win 7 laptop having intermittent startup problems and displaying "PXE-E61: Media test failure, check cable"
-Figure it's probably just a hardware connection problem, but before dismantling to inspect connections more closely, swap HD with the one that has Ubuntu installed
-Media test failure magically goes away. Suspect it's most likely that the bad connection was on the HD's end, glad it's working.
-Laptop goes into circulation for several weeks and has no startup problems.

Anyhow, I'm doing end-of-year check-in and maintenance right now and it is requested that I install win 7 on that computer for consistency's sake. Installation goes smoothly, but once win 7 is installed on this hard drive the same media test failure is immediately back.

It doesn't make sense that the error would be OS-related, since if it can't mount the drive to boot from, it doesn't matter what software is on it. But I did have to reformat the HD as NTFS to install windows on it, and I can see the disk format affecting the ability to mount the drive. It seems like a long shot, but it just seems like too strong of a coincidence that the problem went away and stayed away as long as the disk was ext4-formatted with ubuntu and came right back once the disk was NTFS-formatted with win 7 again.

Any insight or similar experience?

---

### Post by weatherman2 on 2015-06-29
Your laptop can boot from multiple targets: CD, USB, hard drive, and network (and perhaps others).  There is a priority order saved in BIOS Setup, and you can change the order (so you boot from USB before hard drive or whatever.)

The BIOS will try to boot from each boot target in the priority list.  If the first target doesn't exist (or isn't bootable), the BIOS will try the next one in the list.

Network boot is in your list.  When you get the message "PXE-E61: Media test failure, check cable," that means the laptop tried to boot from your network but failed.

In other words: it tried to boot from USB, CD, and hard drive and failed.  Now it has moved on to network boot and failed at that, too.

Translation: your hard drive isn't bootable.  Your Windows installation probably failed for some reason.

It's also possible there is some intermittent issue with the hard drive, the cable, or the controller on the motherboard.  You should test the drive itself to make sure it is healthy.  Try GSmartControl to check S.M.A.R.T.   Make sure there are no serious Attributes highlighted in red.  Run the short S.M.A.R.T. test and maybe the longer one if you have time.

Or try swapping this drive into another identical laptop and try booting it there.  If it fails there too, we might guess the trouble is really with that drive or with your installation.  FYI, there are ways to repair boot problems on a Windows installation - try booting your Windows installation media again and try that.

---

