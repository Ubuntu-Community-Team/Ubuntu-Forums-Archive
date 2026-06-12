---
title: "filesystem errors and related strange behavior"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by pytheas22 on 2007-12-05
Hi all,

For a couple weeks my gutsy system has been doing some weird things:

1. once in a while when I'm working, the system temporarily locks up...the hard drive runs at full speed (as indicated by the hard disk LED) and I can't do anything in the *active* window, which grays out as they do in gnome when they stop responding (other windows besides the one I was working in remain accessible).  After two or three minutes the hard disk light turns off and everything is ok again.  This happens once every ten minutes or so, and as far as I can tell only occurs when I'm working, not when the machine is idle
2. when I boot I have trouble with grub.  sometimes it just hangs with a black screen until I press the reboot button, sometimes it says grub error 17 or grub error 18, and sometimes it says it failed to boot and brings me to the grub command line.  Lately, only about 20% of boot attempts make it past grub successfully.
3. most recently, I've started seeing errors like "buffer I/O error on device sda2, logical block #######" displayed when I press control-alt-F[x]

these problems have gotten progressively worse over the last few days, to the point that today it took a dozen boot attempts before I finally made it to gnome

My hard disk is SATA-300 (I don't remember the vendor) and is about six months old.  SMART is turned on and doesn't give any warnings, nor does BIOS have any problems. detecting the drive.  When I am able to boot successfully, there are no filesystem errors detected.  The drive contains one NTFS partition and two others in reiserfs.

I think it's clear that my problems are related to the filesystem.  My question, however, is this: does this sound like a problem resulting from errors in the software, or is it more likely that my hard disk is going bad?  If it's a software error then presumably a reformat will make it go away, right?  I just don't want to go through that if the issue is really the hardware and I should just buy a new drive...

thanks for any help!

---

### Post by Friek on 2007-12-06
If your system completely hangs momentarily and your kernel is whining about IO errors, your HD is probably dying. How did you check the SMART status?
Try installing smartmontools and run smartctl --all /dev/sda. If it shows errors, it is indeed dying. If it isn't, your IO controller may be causing trouble.
Additionally, if it used to work alright and suddenly doesn't anymore, I'd suspect the HD to be the cause anyway..

Good luck.

---

### Post by pytheas22 on 2007-12-06
Thanks a lot for your help.

I had been looking only at the SMART values reported by BIOS.  I installed smartmontools and the disk passes, although it has more Pre-fail values than I would expect for a relatively new disk.  Maybe it was just not manufactured well (apparently Western Digital is the vendor), because I don't think I've done anything that punishing to it...although it does say that the temperature limits were exceeded at some point in the past, so this could be the problem.

Anyway, it's worth noting that it hasn't acted up at all since I last rebooted yesterday.  I changed the SATA port by which it was connected to the motherboard; maybe that helped for some reason.  I'll probably replace the drive in any case though when I get a chance, because this machine is my main workstation and it needs to be highly dependable.

thanks again for the suggestions

---

