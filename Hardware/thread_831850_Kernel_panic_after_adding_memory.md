---
title: "Kernel panic after adding memory"
date: 2008-06-17
forum: Hardware
---

### Post by tlcain53888b on 2008-06-17
I have a Dell Dimension XP T650r with 128M of memory.  I could not get the 7.10 Live CD to load.  I added memory:  SDR PC100 256M.  I was able to load Ubuntu and have been using it without any problems.

The system is slow, so I tried to add more memory:  Kingston PC133 256M.  When I boot the system, I get a kernel panic.  I booted from the Live CD and ran a memory test - 100% errors.

I removed the new memory module and my system boots fine.  

I'm not sure what my problem is.  Does Ubuntu not support this Kingston memory module?  Is there a compatibility problem between the new memory and one of the memory modules I already have installed?

What do I do next to diagnose the root cause?

---

### Post by s0ury on 2008-06-17
PC100 runs at 100MHz,
PC133 runs at 133MHz. They are incompatible between them.
I suggest that you replace your PC133 with PC100 since PC100 is supported by your motherboard, else, if you are sure your motherboard supports PC133 then you could replace everything with PC133 memories, since they do make a little difference.

---

### Post by ukripper on 2008-06-17
> **tlcain53888b said:**
> I have a Dell Dimension XP T650r with 128M of memory.  I could not get the 7.10 Live CD to load.  I added memory:  SDR PC100 256M.  I was able to load Ubuntu and have been using it without any problems.

The system is slow, so I tried to add more memory:  Kingston PC133 256M.  When I boot the system, I get a kernel panic.  I booted from the Live CD and ran a memory test - 100% errors.

I removed the new memory module and my system boots fine.  

I'm not sure what my problem is.  Does Ubuntu not support this Kingston memory module?  Is there a compatibility problem between the new memory and one of the memory modules I already have installed?

What do I do next to diagnose the root cause?


Could be incompatible with your other memory card. but lets try diagnose.

check your BIOS what it supports and showing 100MHZ or 133MHZ

---

### Post by prshah on 2008-06-17
> **tlcain53888b said:**
>  I added memory:  SDR PC100 256M.  I was able to load Ubuntu and have been using it without any problems.

I tried to add more memory:  Kingston PC133 256M.  When I boot the system, I get a kernel panic.  I booted from the Live CD and ran a memory test - 100% errors.


Try swapping the positions of the two RAM memory. Generally, 133Mhz RAM will run fine at 100Mhz but the reverse is not true. The fact that you're getting 100% errors suggests to me that you've put the 133Mhz RAM in slot 0, and most likely the 100Mhz module is simply being ignored, or forced to run at 133Mhz for which it's not designed.

So you need your 100Mhz RAM to be in the DIMM 0 slot (or whatever the 1st slot is called, it will be marked on the motherboard.). Then place your 133Mhz RAM in the DIMM1 slot. Now your 133Mhz RAM will operate at 100Mhz.

Now, the first thing you need to do is run memtest. If it shows errors, then probably the 133 Mhz module is bad; to test it, remove the 100Mhz modules, keep only the 133Mhz in slot 0, boot and run memtest. If memtest still shows errors, the memory module is bad.

---

### Post by GenesisV2.0 on 2008-06-17
This is going to sound so stupid ok but stick with me ...

when i had this on my old rm gt7000 (yeah ... i know 64mb ram and running ubuntu) i got kernal panics when i put in new memory and in despiration i took the two ram cards out and swopped them around and via some mirical it actually worked -- i know its not the techy answer you were after but it honestly did work for me.

Tell me if it works haha

---

### Post by tlcain53888b on 2008-06-19
I switched the new PC133 memory with the PC100 memory stick in the middle slot on the motherboard.  This prevented the kernel panic when the system booted.  But the system is hanging just after I enter the login name and password.  I booted from the Live CD and ran a memory test.  The test reported an extremely high error rate.

I removed the new PC133 memory, and successfully booted the system.

From the responses I got, it looks like the problem could be a) a bad memory module, b) incompatibility between the PC100 and PC133 memory or c) incompatibility between the PC BIOS and the new memory module.  There doesn't seem to be much point in trying to determine the exact cause.  I'll need to get a new memory in any case.  I will get PC100 memory this time.

Thank you for the responses.

---

