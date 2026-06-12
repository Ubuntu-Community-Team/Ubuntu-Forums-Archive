---
title: "Can't suspend / hibernate if [ram size &gt; swap size] ?"
date: 2008-04-28
forum: Hardware
---

### Post by Gan Quan on 2008-04-28
I'm using uswsusp to do software suspend / hibernate, however I can't get it to work properly. It actually turned my laptop into suspend / hibernate, but I can't recover from those states.

I did some search and found that uswsusp (sort of) puts the memory image onto the swap partition, which may cause my problem because my laptop has 2GB of ram, but my swap partition is only 1GB.

Is there a way to fix this? Any input would be appreciated.

---

### Post by Gan Quan on 2008-04-29
Anyone?
I'm desperate to make suspend / hibernate work..
Thank you

---

### Post by Archmage on 2008-04-29
I think you already provide the information. You need 2 times your ram size in the swap file to make this work.

Either you increase your swap file or you reduce your memory size. :lolflag:

---

### Post by dburnett77 on 2008-04-29
Hardy Heron has adapted to bridge interfacing with GPUs.

The swap has to be accessed more often, as I noticed with my card, it sets a reachable virtual RAM space.  When I added a new 256MB card, it lists hardware info as 512MB.

In order to do this, the RAM area is moved sometimes, and occassionally onto the swap area.

An increase is necessary for normal operation.  I went on a 1GB system:
swap=1.8MB to 2.5 MB and it's stable.

---

### Post by Gan Quan on 2008-04-30
I followed a guide [here](http://en.opensuse.org/NVidia_Suspend_HOWTO), just blacklisted the intel_agp module and now both suspend and hibernate worked. The swap size is still half of my ram size, I don't know why it worked but meh..
However I wonder where the memory image is placed in hibernate mode.

---

### Post by F W Adams on 2009-02-15
Don't forget that if you hibernate it is not strictly necessary to save the whole of ram but only the ram that happens to be in use at the time.

---

