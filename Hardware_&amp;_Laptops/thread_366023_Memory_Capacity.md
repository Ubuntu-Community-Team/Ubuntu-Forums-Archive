---
title: "Memory Capacity"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by chipdip on 2007-02-20
Well, Im about to upgrade my computer from a lowly 512MB RAM to 4GB, and put in a GeForce 7300GT. I was wondering about the memory, I have heard Windows XP can only address 3.2GB of memory. Is there a limit in Linux?

---

### Post by Billi on 2007-02-20
I read somewhere the limit for linux on x86 hardware is 64GB.

---

### Post by tgalati4 on 2007-02-20
Depends.  I think the real limitation is with the 32-bit operating system which limits you to 4GB individual files--important for video editing.  With 64-bit blade systems, you are looking at 32 GB per blade (dual Opteron Sun Fire X4100) or 64 GB (Sun Fire T2000, T1-8 core monster).  I'm sure there are other examples.

Try it and let us know how your system performs.  I would not be surprised if your system becomes slightly less responsive--it depends on your motherboard and chipset.  Some chipsets handle max memory better than others.  More memory means larger page files to sort through and this takes time.  Depending on what you are doing 2GB may be sufficient and faster than 4GB.

The least of window's problems is maximum memory capability.  It will lock up long before reaching those limits with any application.

I routinely edit sound files in Audacity that are 700 MB each--several CD's simultaneously on a system with only 512 MB of RAM.  On another system with 1 GB of RAM the edits are slower because of a slower disk drive.

4GB will simply delay swapping to harddisk, but may cause slowdowns in responsiveness due to the time it takes for the memory bus chipset to address that memory.

Performing some benchmarks at 1GB, 2GB, and 4GB would be instructive.

Let us know.

Terry

---

### Post by az on 2007-02-20
If your motherboard can address the ram, the linux kernel will be able to use it.

---

### Post by chipdip on 2007-02-20
Well, I can list the hardware right now. Once I get everything installed and running I will post some benchmarks. 

Biostar TForce6100-939 Motherboard
AMD Athlon 64 3200+
EVGA GeForce 7300GT
4GB CORSAIR DDR 400 RAM

---

### Post by chipdip on 2007-02-20
> **az said:**
> If your motherboard can address the ram, the linux kernel will be able to use it.

I've never heard that one before. Last I heard, the 32-bit kernel won't recognize all 4GB, and I would need to go with 64-bit. 

From [here:]("http://ubuntuforums.org/showthread.php?t=339474&highlight=64+memory")
> Hi all

I also face similar problem, ugraded my PC memory from 2GB to 4GB, running "top" command reveal that system only have 3574 Mb, where the rest 500 Mb gone?

Ubuntu Version -> Drake
Kernal -> 2.6.15-27-386

Any help will me appreciated

Thanks
James Khoo

---

### Post by az on 2007-02-21
> **chipdip said:**
> I've never heard that one before. Last I heard, the 32-bit kernel won't recognize all 4GB, and I would need to go with 64-bit. 




The 386 kernel in Breezy was able to use 4 Gigs of ram.  That was over a year ago.

When you install ram, you should make sure that memtest86 can test it.  The memory test that is performed by the BIOS is often irrelvant.  

The only limit on addressing the ram is the motherboard.  You can stick in as much ram as you want, but if the motherboard cannot use it all, some of it will be ignored,  If you stick 6 Gigs into a 32-bit motherboard, you will only be able to use 4 Gigs.  Maybe less due to the density and timing - if your MB can only use half of the density, that means 3 Gigs...

Often, though, the amount of ram is overestimated.  For example, if you have mismatched timings, the ram will be detected and the motherboard will try to use it.  Your OS will crash when it tires to use it.  That's why you should use memtest86 to make sure the ram is actually useable.

---

### Post by chipdip on 2007-02-23
> **az said:**
> When you install ram, you should make sure that memtest86 can test it.  The memory test that is performed by the BIOS is often irrelvant.  
Not a problem. Should only take... 6 Hours, right? I'll grab the :popcorn: 
> **az said:**
> The only limit on addressing the ram is the motherboard.  You can stick in as much ram as you want, but if the motherboard cannot use it all, some of it will be ignored,  If you stick 6 Gigs into a 32-bit motherboard, you will only be able to use 4 Gigs.  Maybe less due to the density and timing - if your MB can only use half of the density, that means 3 Gigs...
Also. Not a problem, I already checked all of this out with the manufacturer.
Unfortunately, the memory arrived, but I am not anywhere near the computer now, so I have to wait a while.

---

