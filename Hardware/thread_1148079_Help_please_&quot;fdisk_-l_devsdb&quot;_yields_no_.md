---
title: "Help please: &quot;fdisk -l /dev/sdb&quot; yields no response."
date: 2009-05-04
forum: Hardware
---

### Post by nanninga on 2009-05-04
Hello,

I have three devices.  sda, sdb and sdc.
I used to use sdb with ext2 and it worked fine.
I upgraded to Jaunty and installed a new 1TB sda drive.

I was briefly able to get sdb working but then it would disappear.

Now, when I boot, gparted finds sdb but fails to format it. Then gparted ceases to list sdb in the dropdown menu of devices.

fdisk -l /dev/sdb will not list any information about sdb.  It just goes back to the prompt.

When booting XP, and trying to manage the disk there, I find that at about 80% completion of an ntfs format process, XP will fail.

Does anyone have any advice for me to resolve?  I have the data backed up, so I'm happy to hack away, I just don't see how it would be a physical error since it used to work.

Thank you for your time.
-John

---

### Post by mikedep333 on 2009-05-04
It sounds like your hard drive is starting to have errors.

Under linux, you can run "fdisk -l" and see if it sees it.

Under windows, you can use the program speedfan and run the SMART tests to see if it detects any errors on the drive. You may need to enable SMART in your motherboard bios. Speedfan is available here:
[http://www.google.com/search?q=speedfan&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=speedfan&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by nanninga on 2009-05-04
Hello Mike,
Thanks for your reply.  When I type fdisk -l, sdb is not seen (see below)
[I]
If fdisk -l does not see the drive, does this indicate the drive has a hardware failure?[/I]

Thanks!
-John

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a481a47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375      121601   925560877+   5  Extended
/dev/sda5            6375        8806    19535008+  83  Linux
/dev/sda6          120846      121601     6072538+  82  Linux swap / Solaris
/dev/sda7            8807      120845   899953236   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf5ba776

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38914   312571192+   b  W95 FAT32

Disk /dev/sde: 1200.3 GB, 1200362618880 bytes
255 heads, 63 sectors/track, 145935 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd6a35b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       26125   209846272   af  Unknown
/dev/sde2           26125      145936   962382771    b  W95 FAT32
jd@shiva:~$

---

### Post by mikedep333 on 2009-05-04
So yeah, run the SMART tests with speedfan under windows.

Or you can look through the logs under linux (/var/log/ or the command dmesg) for anything related. I'm not too familiar with doing this.

---

