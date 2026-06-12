---
title: "What do i use to check hard drive for errors?"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by junner18 on 2007-11-18
How do i check my hard drives for errors?  Like the linux equivalent of scandisk of checkdisk.

---

### Post by nick_h on 2007-11-19
fsck

For details type:
```
man fsck
```

---

### Post by junner18 on 2007-11-19
I went through the manual.. and I still couldn't figured out (newbie).  Will this do a surface scan to check the drive for physical problems?

---

### Post by rfruth on 2007-11-19
fsck primarily checks for soft errors (as does scandisk / chkdsk) does your bios support mapping out bad blocks  (a low level scan tool) ?

---

### Post by rsambuca on 2007-11-20
Ubuntu is set to automatically scan your partitions for errors about every 30 boots.  If you want to see how many times a partition has been mounted, you can enterr this command in a terminal:```
sudo tune2fs -l /dev/hda1
```You have to replace the "/dev/hda2" with the actual partitions on your system you want to look at.

---

### Post by junner18 on 2007-11-20
Okay perhaps I should take a step back.  A few months back this hard drive had I bit of a crash, I lost some data.  The BIOS gives me a wanning every boot that it may fail.  I wanted to check it for errors before i started to use it with Linux, but I found that this was not as straight forward as with windows.  What should I be doing?

---

### Post by nick_h on 2007-11-20
Most drive manufacturers provide utilities to check drives.  I suggest you go to the website of your drive manufacturer.

The BIOS is probably reporting that some SMART data field is not within limits.  Are you running Ubuntu or Windows on the machine that the drive is attached to?

---

### Post by rsambuca on 2007-11-20
You can check the drive for errors.  Use the liveCD and run an "fsck -f" on the drive.

---

### Post by junner18 on 2007-11-26
Yes it is a SMART error I am getting, and the manufacturer utility finds lots of errors, but doesn't fix them.  I am running only Ubuntu on this computer, but  I haven't tried the Live CD solution yet.

---

### Post by junner18 on 2007-11-27
The drive is read-only, on live or regular boot.  So I can't used fsck.  I am not able to change this Permission from the properties windows, is there some other way?

---

### Post by rsambuca on 2007-11-27
What command are you using?

---

### Post by az on 2007-11-27
Use badblocks to check a disk.

sudo badblocks -s -v /dev/sda1

Where sda1 is the partition you want to check.  

Badblocks checks the disk.  Fsck only checks the filesystem.

---

