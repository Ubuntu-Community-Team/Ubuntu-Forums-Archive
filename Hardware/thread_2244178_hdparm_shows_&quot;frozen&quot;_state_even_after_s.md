---
title: "hdparm shows &quot;frozen&quot; state even after secure ata erase- BIOS related?"
date: 2014-09-14
forum: Hardware
---

### Post by asadajk on 2014-09-14
I have a 180GB Intel 330 series SSD which I plan to use with Ubuntu Gnome Edition. The problem is, when I use hdparm(version:v9.43), it  shows SSD drive is always frozen. BIOS AHCI mode is used. **I have power cycled(removed sata power cable and immediately re-plug) and did secure erase to unfreeze once. but, on next boot, the SSD drive is "frozen" again.** I have a Intel DH67CL1 motherboard with latest BIOS version.(Supports UEFI, if that helps). What can be done to prevent drive from going "frozen". I was planning to RMA the drive until I thought about the BIOS which may be locking down the drive. 
Additional info: I have a 160GB Seagate Sata hdd and a sata dvd drive also connected to the board. 
```
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        **frozen**
    not    expired: security count
        supported: enhanced erase
    4min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: xxxxxxxxxxxxxxxxxxxx
    NAA        : x
    IEEE OUI    : xxxxx
    Unique ID    :xxxxx
Checksum: correct

```

---

### Post by asadajk on 2014-09-14
my query is, SSD is "freeze locked" by BIOS. I have once secure erased this brand new drive without any Data. So, If I have to continue installation, I've to bypass BIOS(boot livecd and plug in SSD), all after another secure erase? is that correct?

---

