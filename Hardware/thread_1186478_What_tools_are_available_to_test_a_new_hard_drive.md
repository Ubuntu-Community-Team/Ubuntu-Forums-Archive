---
title: "What tools are available to test a new hard drive?"
date: 2009-06-13
forum: Hardware
---

### Post by learningcurb on 2009-06-13
I've recently purchased a new hard drive and I am wondering what programs are able to do some diagnostic testing on it to make sure the drive is reliable and that it hasn't been damaged during shipping.  There's a pretty good program under Windows called [HDTune]("http://www.hdtune.com/"), which seems to do some pretty good testing and benchmarking.  So I wonder if it would be worthwhile to test the drive in Windows, then reformat and install Ubuntu on it.  Or would the reformatting simply delete any test results such as records of bad blocks found?

Also, have there been any cases where diagnostic software has damaged computer equipment?  I'd like to know what **not** to do before I start messing around too much. :)

---

### Post by whoop on 2009-06-13
I use smartmontools for my raid array, it works quite well (as a daemon or manual (or both)). It's not really for benchmarking but it is for checking the health of your disk(s).

---

### Post by SirPaPa on 2009-06-16
Thanks Whoop. I needed this.

---

### Post by rbolio on 2009-06-16
My best guess is that installing ubuntu and running fsck in terminal is a good choice.... I mean when my previous HDD died, fsck was the program that helped me notice how much / what parts died...

Hope it helps!

---

### Post by learningcurb on 2009-06-16
Thanks guys. I checked out smartmontools and found a useful GUI frontend for it at [http://gsmartcontrol.berlios.de/home/index.php/en/Home](http://gsmartcontrol.berlios.de/home/index.php/en/Home) .  I suppose running fsck manually might be a good idea, though I think Ubuntu does this every 30 something mounts?

smartmontools doesn't seem to check for bad blocks though.  Are bad blocks still an issue with linux and modern hard drives?

---

### Post by whoop on 2009-06-16
fsck is run at boot time after a certain amount of boots or a certain amount of time.
> **learningcurb said:**
> smartmontools doesn't seem to check for bad blocks though.  Are bad blocks still an issue with linux and modern hard drives?
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
> 
This article describes what actions might be taken when smartmontools detects a bad block on a disk

You can't expect a hard drive to live forever (especially when you use it)
All (current) hard drives have a finite life (even solid state drives). I don't know how/if/when hard drive failure will occur for solid state drives (I haven't used them yet), but I have read that ssd's support S.M.A.R.T. so it must be useful for ssd's too.

---

