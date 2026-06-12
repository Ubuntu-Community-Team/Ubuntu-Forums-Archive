---
title: "SSD wear leveling - works within a swapfile?"
date: 2021-03-25
forum: Hardware
---

### Post by spamhog on 2021-03-25
Just  a very specific theoretical curiosity.

- SSD
- swapfile on SDD, preassigned as such and left alone at that size
- **does wear leveling work WITHIN the swapfile?**

I guess it doesn't. AFAIU wear leveling is an internal drive phenomenon, should work well enough at the file write - delete - trim level, and within a file the drive shouldn't really know or care or impose another virtual cluster addressing level. But I may err. Maybe the kernel is aware of the nature of the swap space and does some fancy addressing of its own. On a spinning drive, a partition or a non-fragmented swapfile around the same head position might even give some added performance.

NOTE: *Not a question on advisability of swapfiles, swapping, swappiness, swapfile vs partition, whether SSD wear is or isn't an issue, how to optimize performance, partner swapping, moonphases, vampires, da da da :-D*. I very rarely run a monster job that requires swap. If someone does, is it in theory better to assign a huge size to the swapfile, like a multiple of projected use, assuming writes will be spread all over the preassigned sectors that the swapfile is in?

---

### Post by TheFu on 2021-03-25
In short, the physical ideas that we've grown used to with spinning disks and early SSDs haven't applied for years.  They are all virtual blocks these days.  Every time there is a write operation on an SSD, it can be sent to anywhere on the SSD available storage and virtually mapped.

Everything about a modern SSD is virtual as seen by the BIOS and OS.  Wear leveling is an internal thing.  Every block inside the SSD is logically remapped elsewhere.  Also, SSDs are over-provisioned to ensure they can meet their durability/endurance specifications.

There are a few different types of SSD storage - TLC, MLC, QLC, and SLC.  Each of these have different write-count targets which are very well understood. So ... if you buy the SSD with the endurance requirements for the task, don't use every single block (I ignore about 20% as a rule), then the thing will most likely last longer than we care to use it.  How many 128MB flash drives do you still use today?  None.  Because we can get 8G-64G flash storage that is faster for $10.  The 128MB lifespan just doesn't matter anymore.  The same will apply to SSDs.

Since you didn't ask about swapfiles, but did ask about swapfiles - ... er ... I'll assume you can search these forums. About a 8-12 months ago, we had a long thread about swap in these forums.

All this virtual mapping is why data recovery from SSDs is nearly impossible and also why the only way to safely destroy an SSD when we are finished with it is melting it down, completely.

---

