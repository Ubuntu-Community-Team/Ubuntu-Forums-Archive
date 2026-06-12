---
title: "Error after harddisk swapping"
date: 2010-05-28
forum: Hardware
---

### Post by neic on 2010-05-28
Hi.
I have just upgraded my server with two new harddrives. I removed the two old disks and installed the two new ones. On the firsk new disk i made a system partition, mounted at /, a data partition mounted at /l1 and a swap. On the second disk i made a data partition mounted on /l2 and a swap. I then removed the second harddrive and installed one of the old harddrives, when it booted i got a error saying that the disk with /l2 was missing, i skipped it and copyed my data from the old disk to /l1. I did the same with the second old disk. When I afterwards installed the second new disk again it stopped after "Verifying dmi pool data...". I took the second disk out and formated it on a windows machine with "bootrec /FixMbr" and then formated it as "unused" using a ubuntu live cd. I ecspected the /l2 is missing error again, but i got "Errors where found while checking the disk drive for /"!

I am use to work with windows and i guess i should have unmounted /l2 before removing the disk. I do not know I mannaged to screw up the first new disk, though.

Is there some file i can edit to "remount" the disks/partitions in the right places or something?

I am using Ubuntu 10.04 Desktop.
MoBo/CPU: Via EPIA EX15000G
Two old disks: Seagate Barracuda 7200.10 320 GB
Two new disks: WEstern Digital WD20EARS 2TB

---

