---
title: "mount 1 of 2 partitions but NOT BOTH?"
date: 2012-04-17
forum: Hardware
---

### Post by potroastmaster on 2012-04-17
Ok, I am fairly new to Ubuntu and have had success accessing hard drives for people and getting their data backed up for them. But currently I have a hard drive that "S.M.A.R.T." states is failing. Attempted CHKDSK in windows CMD with no success (very super slow and stating that nearly every file searched after the first 3% was "unreadable") took approximately 5 hours to accomplish 4 percent. with dual boot machine opened Ubuntu 10.04 and i am able to mount the recover partition but not the main partition. the drive is Hitachi HDD:5K500.B-250 (250GB) partitions are approximately 239GB for the files that I am attempting to recover and 11GB for the recovery partition of windows 7. and aprox 20mb un allocated partition space. This drive when attempting to boot from it goes to "windows start up repair/recovery" and can not complete the process because the program states "load drivers for the drive so you can use it" and ofcourse efforts were unsuccessful. this computer that hd came out of is an asus EEEPC(netbook). Thanks for your help in advance.

P.S. Currently using Desktop with extra HD power and data cables. for testing/recovery.

Jeff.

---

### Post by Cyclane on 2012-04-18
Try to image the device using ddrescue and when that succeeds try to extract the data from the image.

This will help you:
[https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive)

---

