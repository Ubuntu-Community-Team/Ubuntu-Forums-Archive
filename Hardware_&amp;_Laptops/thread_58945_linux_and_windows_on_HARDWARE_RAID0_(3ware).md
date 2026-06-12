---
title: "linux and windows on HARDWARE RAID0 (3ware)"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by ganja_guru on 2005-08-22
hi this is my config

-3ware Escalade 8506-4LP HARDWARE RAID Controller (SATA)

-4 WD SATA HDD's (250GB each)

-the first two WD's (1 & 2) and the last two WD's (3 & 4) are on seperate RAID0 partitions

- 80GB SEAGATE IDE

-i installed windows on the first two drives (i.e. the first RAID0), and it seemed to install the bootloader on the MBR of the Seagate IDE drive

-i installed linux on the second two drives (i.e the second RAID0), and this overwrote the MBR on the Seagate IDE drive.

Linux boots fine, windows does not

this is NOT a software raid setup so my first RAID0 is recognized as "sda" with windows on "sda1", while the second RAID0 is recognized as "sdb" with linux on "sdb2", while swap is "sdb1"
this works for LINUX in lilo.conf

boot=/dev/hda #(the seagate ide drive)

image=/boot/vmlinuz-2.6.12
       label=linux-raid0
       root=/dev/sdb2
       read-only


however, this does NOT work for windows:

other=/dev/sda1
label=Windows
table=/dev/sda


as a result, im able to boot only into linux.. in the windows recovery console, fixmbr/fixboot dont seem to work. Please help...thanks for your time.

---

### Post by ganja_guru on 2005-08-22
to anyone who cares...this works

other=/dev/hda1
label=windows
table=/dev/hda

---

