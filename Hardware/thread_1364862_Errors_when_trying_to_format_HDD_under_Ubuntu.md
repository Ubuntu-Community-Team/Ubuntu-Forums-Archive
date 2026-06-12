---
title: "Errors when trying to format HDD under Ubuntu"
date: 2009-12-26
forum: Hardware
---

### Post by madprofessor on 2009-12-26
I have a 20GB ATA laptop hard drive. I am trying to format this as ntfs to do a couple of things. When I try to do it under Palimpsest Disk Utility i get this error

> 
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=41126400
Entering MS-DOS parser (offset=0, size=20003880960)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 41094144, type 0xde)
new part entry
looking at part 1 (offset 41126400, size 19954529280, type 0x0c)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=0
Error: Input/output error during write on /dev/sdb
ped_disk_commit() failed

And also I tried under GParted without any success. What could be causing this?

---

