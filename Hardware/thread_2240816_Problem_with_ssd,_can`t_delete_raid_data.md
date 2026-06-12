---
title: "Problem with ssd, can`t delete raid data"
date: 2014-08-22
forum: Hardware
---

### Post by alexander47 on 2014-08-22
I'm trying to install Ubuntu on my ssd drive. 
  The bootloader can't find it but the bios does. From other questions I  got that i have to delete the raid metadata which are definitely on the  ssd cause i checked it with ```
fdsik -l
``` where the ssd was available. 
  Now I tried to use 
  ```
sudo dmraid -E -r /dev/sdb
```
  which gave me
  ```
Do you really want to erase "ddf1" ondisk metadata on /dev/sdb ? [y/n]
```
  entering yes i got the error:
  ```
ERROR: ddf1: seeking device "/dev/sdb" to 92183432265728 ERROR:
writing metadata to /dev/sdb, offset 180045766144 sectors, size 0
bytes returned 0 ERROR: erasing ondisk metadata on /dev/sdb
```
  What could I do to get this command working?
  Thanks!

---

### Post by oldfred on 2014-08-22
Usually that command works to remove RAID meta-data.
But it may be more for BIOS RAID, not some proprietary RAID.

What type of RAID was it?
 And was it from BIOS? Is BIOS in AHCI mode?
or was it Intel SRT? And have you turned that off?

---

