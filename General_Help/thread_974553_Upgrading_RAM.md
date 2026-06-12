---
title: "Upgrading RAM"
date: 2008-11-07
forum: General Help
---

### Post by shortcut144 on 2008-11-07
Just to be sure I don't hit some big failure.  I will be updating my RAM memory (SODIMM) from 256MB to 512MB (this is the max my motherboard with handle).  Do I have to do anything to Ubuntu to make the transformation smoothly?  I am assuming not but I thought I'd make sure.

BTW, anyone running Xubuntu on something like a Pentium 3 with 512MB?  I wanna know how the performance will be before the RAM arrives.

---

### Post by Youresorock on 2008-11-07
I was running my system on 256meg when BOTH of my 2gig dimms went bad a while back.  It was unbearably painful.  Going to 512 will change your life.

I've run Ubuntu 8.04 on a Pentium 233MMX w/ 256meg before.  Not to use so much but as to prove it can be done.  Memory and crappy video card were the problems.  The CPU was fine, rarely maxed out actually.

And yeah, you don't have to do anything to prepare.  just slap it in there.

---

### Post by Yellow Pasque on 2008-11-07
One consideration: if you use hibernate, you may have to resize your swap partition to be at least 512MB if it's not already.

---

### Post by dburnett77 on 2008-11-07
Only thing I can think of is it might have to be configured in CMOS.
At the initial boot, pressing DEL, F2, or some other combination will get into the BIOS settings.  There, you can make sure the RAM is detected correctly.

For Xubuntu, it will handle it accordingly.

Something else to consider, your swap space might need to be increased.  Mine is around three times the size of physical RAM, so you might want to consider adjusting it.

---

### Post by shortcut144 on 2008-11-07
I got 700 or so on my swap.  How do you increase the swap?  Use gparted?

---

### Post by Yellow Pasque on 2008-11-07
> I got 700 or so on my swap. How do you increase the swap? Use gparted?
That should be sufficient unless you do multi-tasking with memory-intensive apps. I personally would not resize it unless I found a scenario where this showed I was out of swap:
```
free -m
```

You would resize with gparted from a LiveCD if you wanted to (preferably after you backed up your important data).

---

### Post by dburnett77 on 2008-11-09
> **shortcut144 said:**
> I got 700 or so on my swap.  How do you increase the swap?  Use gparted?

Yeah, gparted or parted.  Or, like the other poster said use the gparted LiveCD.
Although I seldom use the total swap, since you'll have a larger physical RAM area, it may need to dump more data to the HD.

You can just wait and see if it presents a problem.  Might not.

If you decide to, I'd use the LiveCD like the other poster said, since you can't have the drive mounted, and it can be a pain if you aren't familiar with using partition software.

---

