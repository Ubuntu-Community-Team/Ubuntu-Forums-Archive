---
title: "How to provide for backup BIOS image on /dev/hda?"
date: 2014-10-05
forum: Hardware
---

### Post by bcschmerker on 2014-10-05
I noticed that, for certain motherboards, Award Software provided means of accessing a backup BIOS image from a hard drive ("Award BootBlock BIOS"), in case of problems such as a bad checksum on the primary BIOS image in EEPROM.  I do not know, as of 4 October 2014, whether this backup BIOS image is in the Master Boot Record of /dev/hda or on another (probably hidden) partition.  In the case of my Everex-encased LinUX box, Gigabyte Technology, Ltd., has several downloads for BIOS upgrades for the GA-MA78GM-S2HP, but they are all Microsoft Executable format - don't know whether MS-DOS or OS2/NT; this will be my first attempt at providing for a contingency initial microcode load.

How does one determine the appropriate location on the hard drive (in terms of cylinder, head and sector) for Award BootBlock or competitive initial-microcode-load schemes?  Such a set-up, mass-inplemented by International Business Machines Corporation on certain product lines, may be amenable to Coreboot as well as standard BIOS applications.

---

