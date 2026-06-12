---
title: "Can't set disk to Boot"
date: 2011-05-03
forum: Hardware
---

### Post by dryder on 2011-05-03
Hi,
Setup:
XP - sata5
10.04 - sata1

OK - the steps I did:
1. Started new install of 9.10 intending to do a RAID1 install
2. Partitioned 2 disks (sata 2 and 3) for use as RAID1
3. accepted the changes
4. Aborted the install - (unexpected visitors)
5. Later, changed my mind about RAID, so deleted all partitions and reformatted both drives.
6. Tried to install 9.10 on sata2 - would not set / partition as Bootable
7. Repeated on sata3 drive - same problem.
8. Using Seatools for DOS, reformatted both drives
9. Initialised disks as msdos (one in XP the other in gparted)
10. Still can not set / partition as Bootable

Frustrated. I would be very surprised if using the Alternative Install to set up as RAID did anything physically to the disks that could cause harm. It surely would write to the disk only albeit in an area that only seatols could wipe?
Has anybody any clues why these drives can not be set to boot from?
Many thanks,
David

---

