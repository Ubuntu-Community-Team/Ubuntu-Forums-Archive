---
title: "HTC Magic and other USB mount error - solution"
date: 2009-08-30
forum: Hardware
---

### Post by gregh on 2009-08-30
Posted to help others who may find this issue.

Keywords: HTC Android USB no mount 9.04 jaunty

Hardware: 
Jaunty, kernel 2.6.28-15 and HTC Magic. 

Problem:
The magic appeared to have an intermittent mounting error, sometimes it mounted ok and was visible in nautilus and other times not. 
When it did not mount this message appeared in the logs:

 1518.711034] sd 6:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 1518.711039] sd 6:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 1518.711045] end_request: I/O error, dev sdc, sector 0
[ 1518.711049] Buffer I/O error on device sdc, logical block 0
[ 1518.711059] Dev sdc: unable to read RDB block 0

The problem is - if 2 or more USB data devices are connected at the same time they behave as USB 1.0 and this error happens. Just remove all other USB devices and the HTC will mount properly.
I think this is part of a known kernel problem with USB devices.

-Greg

---

