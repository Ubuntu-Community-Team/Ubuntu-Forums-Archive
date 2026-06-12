---
title: "Can't see external NTFS hard drive"
date: 2009-02-20
forum: Hardware
---

### Post by w i l l on 2009-02-20
Hi,

I'm a complete newbie to Ubuntu - i've just stated using it to try and retrieve data from a hard drive (NTFS I think) (taken from the inside of my Buffallo NAS Drive which I lost access to). I've bought the correct connecting cables and power supply so the hard drive is connected to the PC via a USB cable and also powered with a mains connection so that should be all ok. Unfortunately when I turn on the PC with Ubuntu running from the live CD I don't see the hard drive.

sudo fdisk -l just shows me my Windows hard drive...



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       18845   151308202+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 



How can I find it? I've read through a lot of posts and tried quite a few things (spent about half a day in time so far!). What can I do? Any help appreciated!

Thanks.

---

### Post by cariboo on 2009-02-20
Open a Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

this will print ou the last ten lines of dmesg and it will tell us if the drive is being detected, and if it has a problem.

Jim

---

### Post by w i l l on 2009-02-21
ok here it is - think I typed it wrong the first time. Wasn't sure whether to type 'dmesg l tail -n10' or 'dmesg | tail -n10'


ubuntu@ubuntu:~$ dmesg l tail -n10
Usage: dmesg [-c] [-n level] [-s bufsize]
ubuntu@ubuntu:~$ dmesg | tail -n10
[  160.850852] [drm] Initialized drm 1.1.0 20060810
[  160.911819] pci 0000:01:00.0: setting latency timer to 64
[  160.912388] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[  161.898541] [drm] Setting GART location based on new memory map
[  161.900129] [drm] Loading R300 Microcode
[  161.900173] [drm] Num pipes: 1
[  161.900208] [drm] writeback test succeeded in 1 usecs
[  289.633621] NET: Registered protocol family 10
[  289.635903] lo: Disabled Privacy Extensions
[  300.080010] eth0: no IPv6 routers present
ubuntu@ubuntu:~$

---

### Post by w i l l on 2009-02-21
Any ideas?

---

### Post by w i l l on 2009-02-21
Please!

---

