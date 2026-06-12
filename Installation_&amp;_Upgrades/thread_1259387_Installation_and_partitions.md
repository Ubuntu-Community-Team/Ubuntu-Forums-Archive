---
title: "Installation and partitions"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by UAnovice on 2009-09-06
HI, 
trying to install ubuntu 9.04 dual boot togehter with vista home premium
computer Dell xps, 2 500gb disk in raid.
partitions are recognized with gparted life cd (Vista says: EISA configuration, ntfs (primary), ntfs (primary), unallocated (150 GB), ntfs (logical)
Ubuntu installation sees no partitions
I can't afford to reinstall for now
Any suggestions?

---

### Post by ronparent on 2009-09-06
If you are using the standard live cd as an install disk it is not surprising that gparted doesn't recognize your partitions. The standard answer is that you have to use the alternate cd to install from. 

To install from the live cd you would have to install dmraid while booted to the cd. The proceedure for this is set out for you in this reference: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by UAnovice on 2009-09-07
that worked
thanks

---

