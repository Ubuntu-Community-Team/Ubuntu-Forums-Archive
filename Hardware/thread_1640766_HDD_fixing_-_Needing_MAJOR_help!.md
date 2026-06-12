---
title: "HDD fixing - Needing MAJOR help!"
date: 2010-12-08
forum: Hardware
---

### Post by iBlackSunday on 2010-12-08
So I have been searching and searching for a way to fix my 120 GiB external hard drive for the longest of time and have had no luck. So far, I have tried gparted, parted, windows OS formatting tool, pretty much anything and everything to try and it it working again, but nothing seems to work. I am very new to linux (Ubuntu) and might not be using it to its full potential when it comes to this issue.

If somebody could point me in the right direction to see if this hard drive is 100% gone, or if it is possible to fix it. I am not looking to get any information off of it seeing as how its been through the wringer when it comes to formatting and all the likes. I really really appreciate any help I can get some somebody.

(Sorry for the post in the Dell section. Did not notice this forum and could not find a way to delete that topic)

-iBlackSunday

**EDIT** I decided the hard drive has just gone to **** and I no longer as going to try and fix it. The Disk Utility was what made me decide this. Thanks to all who helped.

---

### Post by iBlackSunday on 2010-12-08
I was able to format it and throw a NTFS file system partition on it that was 8 MBs, but I do not know any commands or programs to see if I could fix the part of the disk that it keeps getting caught up on.

---

### Post by conradin on 2010-12-08
wait,... by fix you mean its broken? Or how to mount it?  can you show use 
```

 ls /dev/sd*


```
or
```

mount

```

---

### Post by iBlackSunday on 2010-12-08
```
ls /dev/sd*
```

iblacksunday@iblacksunday-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1

```
mount
```

iblacksunday@iblacksunday-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/iblacksunday/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=iblacksunday)



I got it mounted after partitioning it with a ntfs file system that was 8 MBs, but I am looking to use the whole thing which there is an error in gparted when I try and format/partition it to its full 111 GiB.

---

### Post by coffeecat on 2010-12-08
> **iBlackSunday said:**
> [CODE]there is an error in gparted when I try and format/partition it to its full 111 GiB.

What is the error? That might give a clue as to what is wrong.

Or try this. Plug the drive in and then open Gparted. Make sure you have your 120GB external drive in the main window and then go to Device > Create Partition Table. Make sure it is set to the default 'ms-dos' partition table and OK that. You will now have a completely unallocated drive, but with a new partition table. See if you can now create a partition in the whole of the 120GB space.

---

### Post by iBlackSunday on 2010-12-08
When I go to Device > Create Partition Table and click 'Okay' it freezes right on the spot and if I let it sit, it go right back to gparted showing my internal hard drive that ubuntu is actually running off of. Also, if this helps any, when I try and add a new NTFS partition table, after it throws the error at me, the drive is no longer in gparted, which leads me to believe it is shutting down but if I just leave it plugged in, the hard drive does not remove itself.

The error that pops up is just something saying "Hey, this didn't work" and tries to send me to a tips page that does not help me at all. Like I said, this hard drive might be toast, but being so new to linux and all, I don't know any commands I can try to see if something is screwed up with it.

---

### Post by coffeecat on 2010-12-08
I may be wrong, but that sounds as though there may be a problem writing to the area of the partition table. Perhaps a bad block has developed there which would indeed be curtains for the drive. Sorry, I can't suggest anything else. Hopefully, someone else may have something more constructive. Bump the thread in 24 hours if no one responds.

---

### Post by iBlackSunday on 2010-12-08
Thank you for what you have tried to help me with. Linux has been by far the best OS I have used and there is so much stuff you can do and I am surprised by the amount of help there is out there. :D

---

### Post by iBlackSunday on 2010-12-08
> Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb1: Input/output error


This is the error code I get.

---

### Post by coffeecat on 2010-12-09
I tried googling that error message. A couple of hits were from people with failing drives. I didn't get beyond the first page so you might want to try a google yourself, but it doesn't look hopeful. Sorry.

---

### Post by conradin on 2010-12-09
The disk utility typically gives pretty good info about whats going on with the disk & its life.
System > Administration > disk Utility. 
from there you can view the SMART Data, ( I recommend you do), perform benchmarking, check files systems, and do other disk type tasks.

---

