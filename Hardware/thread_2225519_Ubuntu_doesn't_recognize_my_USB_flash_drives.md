---
title: "Ubuntu doesn't recognize my USB flash drives"
date: 2014-05-21
forum: Hardware
---

### Post by Nz! on 2014-05-21
Hi, I just recently installed Ubuntu 14.04 alongside Windows 8 on my Lenovo Ideapad Flex 14, when I connected my 8Gb Kingston USB flash drive to my laptop, it didn't recognize it at all, nothing happened; I tried unplugging and plugging it again, but it doesn't recognize it, I tried with another USB I had laying around, but no luck. I'm kinda worried since the installation wasn't all that smooth, though everything but the USB's are apparently working. What's wrong?

I read in other threads how they were asking for ***lsusb***:```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And *sudo **fdisk -lu***, which results are kinda confusing for me:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2b541454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

If I need to give more information, just ask :P
Thanks in advance for your help :smile:

---

### Post by squakie on 2014-05-22
The USB not mounting thing is a known problem - however, I haven't seen it not at least show the physical hardware when plugged in.  Were the results of lsusb you showed with the device plugged in?  The device does need to be plugged into a USB port to show in lsusb.  Also, if it doesn't show, do any of the following show anything (remember the device must be plugged in):

sudo blkid

sudo df -h

Do you see anything in those outputs that might be your flash drive (I start by looking for the size)?

---

### Post by Nz! on 2014-05-22
So I just restarted my PC and apparently it works now o_o I have no idea what I did, but it is recognizing the USB I plugged in! I'll update if I figure it out.

---

### Post by squakie on 2014-05-22
Great!  Wish it was that simple with my camera!  ;)

---

