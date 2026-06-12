---
title: "Mounting fakeRAID array with NTFS"
date: 2009-10-30
forum: Hardware
---

### Post by AndyM3 on 2009-10-30
First of all, yes I searched Google and the forums and I haven't found an answer to my question.
A few hours ago I've installed Ubuntu Karmic on my VAIO VGC-RC210G PC via Wubi. I have Windows Vista on the main (fake) RAID0 array and Ubuntu on another drive (along with my media files).
dmraid seems to be working, it recognises my Intel fakeraid, but I can't mount it. Console log here:
```
root@ubuntu:/dev/mapper# dmraid -r
/dev/sdb: isw, "isw_bjgfjedfji", GROUP, ok, 312581806 sectors, data@ 0
/dev/sda: isw, "isw_bjgfjedfji", GROUP, ok, 312581806 sectors, data@ 0

root@ubuntu:/dev/mapper# dmraid -ay
RAID set "isw_bjgfjedfji_Volume 0" already active
RAID set "isw_bjgfjedfji_Volume 01" was not activated

root@ubuntu:/dev/mapper# dmraid -tay
isw_bjgfjedfji_Volume 0: 0 625154560 striped 2 256 /dev/sda 0 /dev/sdb 0
isw_bjgfjedfji_Volume 01: 0 625149952 linear /dev/mapper/isw_bjgfjedfji_Volume 0 2048

root@ubuntu:/dev/mapper# ls -la      #this is /dev/mapper
total 0
drwxr-xr-x  2 root root      80 2009-10-30 17:20 .
drwxr-xr-x 18 root root    4460 2009-10-30 17:32 ..
crw-rw----  1 root root  10, 60 2009-10-30 18:45 control
brw-rw----  1 root disk 252,  0 2009-10-30 17:20 isw_bjgfjedfji_Volume 0

root@ubuntu:/dev/mapper# mount -t ntfs /dev/mapper/isw* /media/raid_vol0
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_bjgfjedfji_Volume 0': Invalid argument
The device '/dev/mapper/isw_bjgfjedfji_Volume 0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```
Note the output of "dmraid -ay". How can I activate the second entry? Because I bet that is the problem.
Also, GParted says I have two volumes on the RAID array: an unallocated thing (probably recovery info used by the BIOS) and the device that was not activated by dmraid (it has a warning sign next to it).
Might be a noob-ish problem, but please help me! I don't want to go back to Vista again due to poor hardware support!

Thanks in advance! Andy

EDIT: Problem solved.

---

### Post by AndyM3 on 2009-10-30
Doesn't anybody know? I really don't want to be stuck with any DRM-plagued, evil, proprietary and unsecure Microsoft creation.

---

### Post by AndyM3 on 2009-10-31
Nevermind, I got it working!
The problem was the RAID array's name "Volume 0" had a space in it. I renamed it to "Volume0" and now Ubuntu automatically detects it and can mount it.

---

