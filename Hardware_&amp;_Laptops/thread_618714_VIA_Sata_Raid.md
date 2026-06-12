---
title: "VIA Sata Raid"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by ryanlhjess on 2007-11-20
I have a VIA VT6420

For some reason my sata raid does not mount,  could someone help me diagnose the problem and maybe come up with a solution.  Im not sure if its a driver issue, or if i just have to mount it, or if linux doesn't support ntfs sata raid

---

### Post by colo on 2007-11-20
dmraid might help you start the array: [http://packages.ubuntu.com/gutsy/admin/dmraid](http://packages.ubuntu.com/gutsy/admin/dmraid)
The problem with this is that your RAID is acchieved not by using dedicated hardware abstracting all the storage logic away from the OS, but rather a special combination of a dedicated fakeRAID-BIOS, metadata specific to that BIOS on your disks, and a Windows-Driver to get all the lump up and running.

---

### Post by ryanlhjess on 2007-11-21
Hey

whoa, that a lil intense, care to give me a hand with what you mentioned?   Any other ideas people?

should i use -a to activate in dmraid?  whats the risks ?

---

### Post by psusi on 2007-11-26
Just installing the dmraid package will automatically run dmraid -a for you and activate access to the raid set.  If you want to install on one, read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

