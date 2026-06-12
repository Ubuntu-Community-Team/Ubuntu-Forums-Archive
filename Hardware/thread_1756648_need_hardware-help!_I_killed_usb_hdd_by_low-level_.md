---
title: "need hardware-help! I killed usb hdd by low-level format"
date: 2011-05-12
forum: Hardware
---

### Post by Martiini on 2011-05-12
ok, so .. 
.. in case any "hardware-pro" is capable of helping with this ..
Im not sure .. but .. I think ..
I killed usb HDD by low-level format

currently HDD drive is unusable

I wanted to "wipe" WD 2500BEV External hdd (Model: WDC WD2500BEVS-22UST0)
I used windows utility [http://www.softpedia.com/get/System/Hard-Disk-Utils/HDD-Low-Level-Format-Tool.shtml]("HDD Low Level Format Tool")
windows says "need to initialize the drive" "unable to initialize because of I/O error"
ubuntu gparted reads the disk but is unable to allocate filetable

root@dell:/home/martin# badblocks -v /dev/sdc
..gives an endless row of numbers ..

"disk utility" SMART data - "disk is healthy"
I ran "disk utility" "extended self-tests" which showes the "disk is healthy"

..so .. Im guessing I need to low-level format the drive again ... ??

---

### Post by Yellow Pasque on 2011-05-12
[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)

---

### Post by Martiini on 2011-05-12
> **Temüjin said:**
> [http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)
exactly .. drive is dead .. me thinks

# dd if=/dev/zero of=/dev/sdc
dd: writing to `/dev/sdc': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00978279 s, 0.0 kB/s

"disk utility"
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error

---

### Post by abohsin on 2011-05-12
Ok ,let's clear things a little, performing a low-level format does not kill a hard disk, it just wipes out the partition table. Wiping the partition table does not allow access to the hdd, but this is because it needs to be reconstructed. Now, that we don't presume there is a dead-end problem, let's analyze which tools to use. Gparted is great, but not really low level partitioning tool. Try getting the raw path of the hdd while it is connected '/dev/sda' for e.g. from Gparted, or from command line 'df -h'. Now use fdisk to create a new partition and thus re-write the partitioning table using 'sudo fdisk /dev/sda'. Then tell us how things went.

---

