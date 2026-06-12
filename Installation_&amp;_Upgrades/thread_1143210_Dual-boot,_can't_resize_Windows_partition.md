---
title: "Dual-boot, can't resize Windows partition?"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by donsy on 2009-04-29
Recently I attempted to install Hardy 8.04.2 as a dual-boot with WindowsXP SP3. Everything is fine until I get to the partitioner section where I have the following options:

o Guided - use entire disk
     - o SCSI1 (0,0,0) (sda) - 30.0 GB ATA Hitachi HTS42403

o Guided - use the largest continuous free space

o manual

Nowhere is there an option to resize my Windows partition (partition 1) and use the freed space. Why isn't that option available to me? Am I missing something?

---

### Post by Mark Phelps on 2009-04-30
Can't answer your questions per se, but in my experience, the safest thing to do is to boot from the LiveCD and do the partitioning stand-alone.  That way, you can boot back into XP after that and confirm that it's still working.  You don't run the risk of accidentally overwriting the XP installation as a byproduct of installing Ubuntu.

Also, I had similar problems with the LiveCD, so I downloaded and burned the Alternate CD.  Only has a text-mode windowed interface, but it did a much better job of recognizing my existing partitions.  Either way, you end up with the same stuff installed, you just don't get the same graphics during installation.

---

### Post by donsy on 2009-05-03
Solved ... I had the hard drive mounted at the time. When you try to install from the live CD with the hard drive mounted your choices are limited. Unmount the HD and you have the option of resizing the Windows partition. This is true for 8.04.2, I don't know about how other releases would handle it.

---

