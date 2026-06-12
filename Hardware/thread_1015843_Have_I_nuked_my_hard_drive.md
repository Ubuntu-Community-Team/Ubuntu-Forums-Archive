---
title: "Have I nuked my hard drive?"
date: 2008-12-19
forum: Hardware
---

### Post by Igniteflow on 2008-12-19
Hi guys, 
I have a desktop using a Gigabyte GA-MA790X-DS4 mobo, which up until now has been running fine. Is has two 500 GB hard drives with a Linux installation on each, running on SATA connections.  Yesterday, I plugged an old hard drive into the IDE cable and powered up the system to see if I could get at my old music. The disk was broken and made some weird sounds so I powered down and removed it.  The problem is that now my system is only detecting one of the two SATA drives even though I have removed the old drive - is it possible that plugging in the defective drive could have nuked one of my disks?  I've tried swapping the SATA and power cables over, but the system still only registers the same single drive.
I've been trying different BIOS settings, but so far I'm not getting anything.  I also tried booting up with a LiveCD and using GParted, but even that doesn't see the other drive either.  
If anyone has any suggestions, I'd love to hear them as a lot of my work is on that disk.

---

### Post by taurus on 2008-12-19
Check the cables again to make sure everything is plugged in and secured properly.

---

### Post by Igniteflow on 2008-12-19
Checked, but still only recognising one hard drive. Any ideas?

---

### Post by taurus on 2008-12-19
Have you tried removing the "good" one and see if the BIOS detects the other SATA drive?

---

### Post by Igniteflow on 2008-12-21
I tried booting just with the good one which of course works fine, then just with the bad one.  The comps not recognising the bad drive at all, so am thinking somehow plugging the broken drive in to the IDE must have blown the electrics to the SATA drive.  Unless anyone has a better suggestion, I think I'm going to replace the hard drive and start over??

---

### Post by abn91c on 2008-12-21
> **Igniteflow said:**
> Checked, but still only recognising one hard drive. Any ideas?
remove the CMOS battery to clear the bios, that should do it, also check the motherboard manual you may have to remove a jumper as well

---

### Post by Igniteflow on 2008-12-23
I removed the battery and jumpers and looked at the manual, but the HD is still dead.  

> **abn91c said:**
> remove the CMOS battery to clear the bios, that should do it, also check the motherboard manual you may have to remove a jumper as well

---

### Post by abn91c on 2008-12-23
the only other suggestion I have is just connect that hdd by it self, set bios to auto detect HDD if you ahve that settings and see what happens then. No detection = dead HDD :-(
also check the jumper settings on the drive, set to master

---

