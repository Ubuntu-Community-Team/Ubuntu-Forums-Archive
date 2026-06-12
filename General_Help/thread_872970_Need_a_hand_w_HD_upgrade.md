---
title: "Need a hand w/ HD upgrade"
date: 2008-07-28
forum: General Help
---

### Post by kulturloseramerikaner on 2008-07-28
I've been running my system now for about a year and a half with two 160 GB drives, one for Ubuntu and the other for Windoze. I just picked up a 500GB on the cheap intending to clone my Windoze partition over to it and remove the old drive as it had gotten full, or maybe repave it and try a BSD or Haiku out just for fun.
I used Clonezilla to make the move last night, but after everything was said and done, the old drive had to stay or else I could not boot.  Removing the old drive gave me a "partition not found" error in GRUB; I switched the cable from sda where Win is to the sdc where I put the clone, which gave me a screen that just said "GRUB" over and over again.
I know this is possible to do; what step(s) did I miss here?  Should I just DD instead and be done with it?
Thanks in advance.

---

### Post by kulturloseramerikaner on 2008-07-28
Well I got impatient and tried a "dd".  It stopped after 20 sec, saying that it had copied 1.1 GB and that sdc was full.  Huh?  When did dd ever care, isn't that what it does?

---

### Post by kulturloseramerikaner on 2008-07-31
Got her working; here's what I did for those who are interested or maybe wondering how to do it themselves:
I ran a second dd after using gparted to delete all partitions manually on the disk, and had a successful copy.  I then used gparted to expand the new Windoze partition to fill the 500GB.  I switched the SATA cables so that the 500GB was in the "0" slot on the mobo, sdb where 'buntu resides is on slot 2, and the old Windoze drive I left unplugged to make sure I truly was booting from the new drive.  Sure enough, that did the trick; Windoze ran chkdsk immediately upon boot, which I just let run, then made sure I ran all the utilities like defrag that I've gotten used to not having to worry about. I opened a few big programs just to make sure there wasn't any corruption, and so far so good.  Btw, Windoze really depends on having a lot of free disk space to run efficiently for some reason; my boot time dropped quite a bit.
I think in the future I'd be better off using Clonezilla as opposed to dd, for the simple fact that Clonezilla will create the clone from an image file, avoiding the problems that could have occurred if I'd had bad sectors on either disk.  But I'm not complaining about the results...

---

