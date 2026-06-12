---
title: "Regular Formatting problem with WINDOWS XP."
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by praveenkoduru on 2007-08-31
Problem:
When I tried to format 40GB Seagate Harddisk with FAT32 in Windows Xp, I am
getting "unable to complete formatt". This error I am getting only
with regular format. With quick format every thing is normal. I Tried
regular format & quick format in Windows Vista, It was formatting
normal for both. The problem is on Windows Xp. In Linux Host also I
tried with mkfs.vfat it was done succesfully. Hard disk is
connected through usb port and i am trying to do regular format after
the window pop-up in Windows XP. Moreover hard disk is like usb gadget
with g_file_storage driver. OS in the gadget is Linux and OS in host
is Windows XP. and please let me know still any more information to be
needed. I tried to debug the
problem. So, the observations are listed below

Observations:
In Windows Vista:
1. For Regular format:
The following SCSI commands were called,
TEST_UNIT_READY, MODE_SENSE_6, READ10, continuous WRITE10. and the
format was successfull

In Windows Xp:
1. For Regular Formatt:
The following SCSI commands were called,
TEST_UNIT_READY, READ10, MODE_SENSE_6, READ_CAPACITY, and continuous
VERIFY and finally displaying "unable to complete the format".
In VERIFY command it was verifying the
different logical block addresses for different times of formatting.
In 10 bytes of command data block, only LBA is changing nothing else
was changing.I dont what windows XP was expecting from verify, and why
is it reading differrent lba's for different times and why is it
unable to complete the format?

Thanks
Praveen.

---

