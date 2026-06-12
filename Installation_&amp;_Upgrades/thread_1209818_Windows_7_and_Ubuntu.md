---
title: "Windows 7 and Ubuntu"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by Klapvee on 2009-07-10
Hello,

I was wondering if its possible to install Ubuntu next to my Windows 7 installation.
Because i have an extra 10 GB free on my hdd and i thought i could try out some Linux OS.

The thing is i've 3 partitions on my HDD.
100 GB -> Windows 7 (Can't Resize)
120 GB -> Data (Can't Resize)
10 GB -> Free.

I wish to install Ubuntu on that 10GB Free space, and after some reading on the internet it seems like a Linux OS needs 2 partitions, 1 for its SWAP file and the other one for the OS itself(?).

So i was wondering if its possible to install Ubuntu on that 10GB without creating 2 partitions?...

Thanks in Advance.

Kind regards,
Klapvee

---

### Post by raymondh on 2009-07-10
> **Klapvee said:**
> Hello,

I was wondering if its possible to install Ubuntu next to my Windows 7 installation.
Because i have an extra 10 GB free on my hdd and i thought i could try out some Linux OS.

The thing is i've 3 partitions on my HDD.
100 GB -> Windows 7 (Can't Resize)
120 GB -> Data (Can't Resize)
10 GB -> Free.

I wish to install Ubuntu on that 10GB Free space, and after some reading on the internet it seems like a Linux OS needs 2 partitions, 1 for its SWAP file and the other one for the OS itself(?).

So i was wondering if its possible to install Ubuntu on that 10GB without creating 2 partitions?...

Thanks in Advance.

Kind regards,
Klapvee

Yes.  

Assuming you only have 2 partitions (the 3rd being free), both Ubuntu root (/) and SWAP can be PRIMARY partitions and still be within the 4-max limit (partitions per HD).

Even if you have 3 partitions (say you forgot about the usual  windows 'recovery' partition), you can make the 10GB space into an EXTENDED partition and install inside it ... thus making SWAP and ROOT logical partitions.

See this link.

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I know you only are giving Ubuntu 10GB.  If you give SWAP 1-2GB, then you're left with just 8Gb (less administrative deductions).  It's very much possible.  Just remember "small space" when you do add apps, files, etc, as you can/may soon run out of space with all those cool, free applications ;)

Good luck.  Back up your files first..... and Happy ubuntu-ing.

---

