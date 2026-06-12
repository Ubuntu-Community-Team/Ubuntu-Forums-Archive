---
title: "When do hard drives spinning down?"
date: 2013-03-13
forum: Hardware
---

### Post by IHateSigningUp on 2013-03-13
I'm about to buy parts for a new home server.  I'm planning to use Ubuntu.  Power usage/heat is a concern.  I want to keep it low.

For the OS, I'll use an SSD.  For cold storage, I'm planning on setting up Samba and an array of hard drives.
Specifically, I'm planning on 4 Western Digital Green 3TB drives on a RAID 10 (ten) array.
90% of the time, these 4 hard drives will not be in use.  These disks will only have files that are infrequently accessed.
According to the spec sheet:
[http://www.wdc.com/global/products/specs/?driveID=927&language=1](http://www.wdc.com/global/products/specs/?driveID=927&language=1)

Read/Write 6.00 Watts
Idle	5.50 Watts
Multiple by 4 and I'm using a full 22 Watts at "Idle".

First question: Will the Ubuntu automatically spin the drives down if no programs are actively reading/writing?  I'd like to spend as much time in the "Standby 0.80 Watts" zone as possible.  Does RAID make a difference?  I'm assuming that "Standby" is the same as "spun down".

Second, Any potential problems with my plan? 1 SSD for the OS and RAID 10 for 6TB of storage?  I will need a GUI from time to time, so I might install the desktop version instead of the server. (For work, I need a back-up desktop machine on occasion, so I need a GUI.  I do not want to buy two machines.)  btw. I'm new to Ubuntu.

Third.  The spec above has: "12 VDC" and "Read/Write 1.78 A".  It was a long time ago, but when I was in college that would mean the drive uses 21.36 Watts (12V x 1.78A).  21.36 Watts is a lot more than the claimed 6.00 Watts.  Is this a sloppy typo? Or am I missing something?  I ask because I need to know the max power the 4 drives will require.

Cheers!

---

