---
title: "RAID-0 on Intel Matrix RAID with Hardy"
date: 2008-07-09
forum: Hardware
---

### Post by linuxkrn on 2008-07-09
Hi all,

Need some help here.  I'm trying to install Hardy on a Dell M1730 with Intel Matrix Raid ```
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 02)
```
Running a RAID-0 stripe on Dual Samsung SSD RBX Series 64GB Drives.

These drives have an existing working Windows XP Partition that I plan on resizing for ubuntu install.  Problem that I have is that dmraid/fakeraid doesn't understand the array information.

I've been following these guides: 

[http://help.ubuntu.com/community/FakeRaidHowto](http://help.ubuntu.com/community/FakeRaidHowto)

which lead me to this page:

[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

I have followed the guide, located the exact Array information sectors. 

```
# dd if=/dev/sda skip=125045422 | hexdump -C | head
00000000  49 6e 74 65 6c 20 52 61  69 64 20 49 53 4d 20 43  |Intel Raid ISM C|

00000010  66 67 20 53 69 67 2e 20  31 2e 30 2e 30 30 00 00  |fg Sig. 1.0.00..|

00000020  7b b8 ba 07 e0 01 00 00  8f 66 c2 f8 a1 00 00 00  |{........f......|

00000030  f0 0f 00 00 00 00 00 c0  02 01 02 00 00 00 00 00  |................|

00000040  8f 66 c2 f8 00 00 00 00  00 00 00 00 00 00 00 00  |.f..............|

00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

*

000000d0  00 00 00 00 00 00 00 00  45 30 4a 38 31 36 53 45  |........E0J816SE|

000000e0  38 31 36 47 37 32 35 38  b0 0a 74 07 00 00 00 00  |816G7258..t.....|

000000f0  3a 05 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |:...............|

```


Before patching, dmraid told me this:
```
ERROR: isw: Error finding disk table slot for /dev/sdb
ERROR: isw: Error finding disk table slot for /dev/sda
No RAID disks
```

I then tried patching dmraid code per the guide.  So the dd copied the last 1024 bytes, so 1024 / 512 (per sector) = 2.  

After patching #define ISW_CONFIGOFFSETS in the code (isw.h) and recompiling, I only get.

```
No RAID disks
```

It had ((di->sectors – 2) << 9).  So unlike the guide had sectors from end, it looks like it just shifted di sectors – 2.  I've tried both (di->sectors – 2) and 2.  Neither worked.  

I've attached all the information I've found so far.  One interesting node is that fdisk -u -l /dev/sda gives me no output.  But the same command on sdb gives me the proper output.  Please let me know how to proceed from here.  Or if you need any more information.

Thanks!

Information:
[http://www.linuxlogin.com/public/array.hexdump](http://www.linuxlogin.com/public/array.hexdump)
[http://www.linuxlogin.com/public/array.dd](http://www.linuxlogin.com/public/array.dd)
[http://www.linuxlogin.com/public/sdb.fdisk](http://www.linuxlogin.com/public/sdb.fdisk)
[http://www.linuxlogin.com/public/dmraid.info](http://www.linuxlogin.com/public/dmraid.info)

---

### Post by linuxkrn on 2008-07-14
Don't everyone reply at once now. :D

---

### Post by linuxkrn on 2008-08-13
Well, 

I've solved my problem but didn't fix the bug.

Turns out that for some reason dmraid was reading an extra four characters on my hard drive serial numbers and thus didn't match up.

Hacking the code  (lib/device/scsi.c) and changing the offset pointer from +1 to +5 resolved my "No Disks" problem.

However, I then soon found out that the default initramfs was also missing dmraid.  So I had to rebuild that and then was finally able to get everything working.

So the bug still exists for dmraid (developer has been notified) so this fix was for my setup only.

So at the end of the day, I've got Fakeraid RAID-0 working with XP and Ubuntu.  Although it was painful.

---

### Post by psusi on 2008-08-15
Nice work on solving it yourself.  This is a known bug I have been working on getting resolved for a while now.  It seems that some hard disks appear to have funkey non ascii characters or spaces in the serial number.  For some reason dmraid removes the spaces ( and I think considers some of the non ascii characters as spaces as well ) when it tries to compare the serial number of the disk with that recorded in the on disk metadata.

I'm still waiting for the upstream author to catch up on his email now that he is back from vacation and remove the whitespace removal.

---

