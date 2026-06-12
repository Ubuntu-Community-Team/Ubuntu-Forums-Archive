---
title: "shrinking a SafeBoot-ed Windows Partition"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-03-24
FYI:
Just purchased Acronis Disk Director Suite 10.0, a disk-repartitioning tool (amongst other things) for $49.99. [http://www.acronis.com/homecomputing/products/diskdirector/](http://www.acronis.com/homecomputing/products/diskdirector/)

Acronis successfully was able to shrink the live Windows XP partition that had been previously SafeBoot-ed. (full partition encryption)

Both Windows when it booted up and the Live LinuxCD recognized the smaller partition size! (that's a good thing)

I was skeptical that the re-sizing, specifically the editing of the MasterBootRecord, would not persist; that SafeBoot would override it or it would be ignored. Evidently not.

I don't know if SafeBoot itself has any tools to do this, as it is our HelpDesk department that does that and they were not forthcoming with any information related to that.

I have not installed Linux on this test machine, yet, but I don't foresee any issues, as long as both sides know how big the partitions are.

When I did run the LinuxLiveCD, it does not give you the slider bar, as it does not recognize the smaller partition as being a Windows partition. This is expected, as that partition is encrypted. But one would go into the manual setup, where the partitions sizes are correctly given, etc.
At this point, I have successfully installed Linux. But I have gotten to this point a different way. When HelpDesk, plans ahead, and creates a spare partition for me for Linux, and then SafeBoots just the Windows partition. (SafeBoot only does partitions, not the whole drive)

Aside: I was forced to do this solution, as the Wubi installer failed for me. I will start a different thread for that problem.

---

