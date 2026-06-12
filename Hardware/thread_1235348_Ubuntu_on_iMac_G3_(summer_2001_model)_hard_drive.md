---
title: "Ubuntu on iMac G3 (summer 2001 model) hard drive?"
date: 2009-08-09
forum: Hardware
---

### Post by cr0ss on 2009-08-09
Hello, I'm considering running the PPC variant of Ubuntu on my mac.  One thing I'm wanting to do is upgrade the hard drive.

It's using a 20GB hard drive right now, and I need to use something bigger, maybe a 120GB just to avoid the G3's hard drive capacity limit.

I have, on the other hand, researched a little to find that if a larger (than 128GB) hard disk is used, then it can simply have one partition formatted under the OSX partition manager (install CD) as 128GB for system use, and the other partition will work no trouble in OSX as it will see that as a separate disk (so I have read anyway, anyone know if this is true in practice?).

What I am wondering though, is:  Would I need to partition the drive under Linux in this same manner?  Will a 320GB hard drive be treated the same way if it's partitioned in Linux as it were in OSX?

---

### Post by cr0ss on 2009-08-09
bump

Any ideas?

---

### Post by ZaHACKieL on 2009-08-09
Maybe I understood your question but...mmm....do you mean you are trying to have a dual boot HD with OSX / Linux ?

If that's your issue I think it's almost the same as when you have a Win/Linux dual boot HD.

Maybe the simplest thing would be dividing your HD in 2, half for OS X and half for Linux. I would first install the OS X in the first half, leaving the other half as unallocated space so, after you have your OS X installed, run the Ubuntu installation and choose that option that says something like "Use Largest Continuous Free Space" and it will install the Ubuntu in the other half.

I hope this helps you, if not, keep asking =]

Let me know what happens

ZL

---

### Post by cr0ss on 2009-08-09
> **ZaHACKieL said:**
> Maybe I understood your question but...mmm....do you mean you are trying to have a dual boot HD with OSX / Linux ?

If that's your issue I think it's almost the same as when you have a Win/Linux dual boot HD.

Maybe the simplest thing would be dividing your HD in 2, half for OS X and half for Linux. I would first install the OS X in the first half, leaving the other half as unallocated space so, after you have your OS X installed, run the Ubuntu installation and choose that option that says something like "Use Largest Continuous Free Space" and it will install the Ubuntu in the other half. 

I hope this helps you, if not, keep asking =]

Let me know what happens

ZL

What I mean is that the G3 EFI/mainboard is limited to seeing 128GB max on the main disk itself.  While (supposedly) a larger drive can be formatted into two partitions in OSX (as long as it's 128GB for the system file or lower, second partition can be any size from my understanding) - it will see the second partition as a second disk and therefore won't be a hassle to use, say a 320GB hard disk in a G3 imac.  I've read mixed reviews on it, so I'm not too sure (so I'm doubtful if anyone's actually done it, or just talking smash)... I'm thinking that partitioning will have to be done outside the computer itself though (hook it up to an enclosure and use gparted), since the limit's at the hardwar/EFI level.

As for usage, I'm likely to stick to Ubuntu with no dual boot (no OSX installs at all, but will have an OSX dvd in case anything goes awry).  It would likely have to be separated into multiple partitions... but I'm really wondering if Linux will see, and be able to use the partitions?  As in, give Linux (just for example) 128GB to system partitions, and the rest of the drive (will say we're using a 320GB hard disk for arguments sake) to whatever (home directory, extra files, media content etc.).  128GB partition would be read perfectly by the EFI/mainboard.  But that second partition - would it work in Ubuntu as it would in OSX?

---

### Post by cr0ss on 2009-08-09
It was hard to find but I think I found it here...
[http://ubuntuforums.org/showthread.php?t=1113139](http://ubuntuforums.org/showthread.php?t=1113139)

So yes, I have to format the first partition to less than 128GB (in the case of using a > 120GB hard disk).

---

