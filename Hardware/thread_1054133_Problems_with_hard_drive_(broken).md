---
title: "Problems with hard drive (broken?)"
date: 2009-01-29
forum: Hardware
---

### Post by UeB on 2009-01-29
Hallo,

I have problems reading some files on a hard drive of mine. So I used smartctr to read information form the disk. I am not sure what do with these informations in other words what action I should take to prevent data loss (maybe some files are already lost I am not sure).

The infos are ambivalent. On the one hand it says:

```
SMART overall-health self-assessment test result: PASSED
```

On the other hand:

```
ATA Error Count: 715 (device log contains only the most recent five errors)
```

and

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      7183   
```      -


I attached the full output text.

Thanks in advance!

---

### Post by cariboo on 2009-01-29
If you suspect the hard drive, go to the manufacturers web site and download their diagmostic software and run it to check the hard drive's health.

Jim

---

### Post by UeB on 2009-01-29
The manufacture's diagnostic tool is for MS-DOS only:
[http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html](http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html)
and the disk is in an usb dive case  (icy box) just to read the smart data I posted I had to put it into a friends PC because this data is not accessible through USB and I have only a notebook. So I suspect that the diagnoses tool also only works if the disk is connected to an IDE controller on the motherboard.

---

