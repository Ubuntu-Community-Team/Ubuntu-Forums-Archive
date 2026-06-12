---
title: "RocketRaid and 9.1"
date: 2009-12-14
forum: Hardware
---

### Post by topkatz on 2009-12-14
I have a rocketraid 1740 hardware sata raid card running on 9.1.  I'm using the open source drivers for the device that can be found on the cards site.  When a new set of kernel headers gets released I have to re make install the drivers again.  Currently I do this after the update and subsequent reboot.  

This is causing issues with the raid.  After the reboot I remake and install the driver, and then reboot again.  Some times the raid is fine, other times it needs repair.  What I want to know is should I be doing the make install of the driver before I reboot after the kernel update?  Will the make install find the header files?  

How should this be handled?

---

### Post by topkatz on 2009-12-15
bump

---

