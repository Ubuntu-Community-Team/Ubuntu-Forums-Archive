---
title: "USB Key (Verbatim Store 'n Go) Won't Mount"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by skjantzen on 2006-02-25
When I plug in my USB key, the light comes on which indicates that it has connected with the computer. When I go to "Places" --> "Computer" a window opens which has an icon entitled "VBTM Store 'n Go Pro" is present. When I click on the icon I get the message:

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted." 

I click the "Show More Details" button and get the following:

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I enter "dmesg | tail" in a terminal window, I get:

[4295322.560000] VFS: Can't find ext3 filesystem on dev sdb.
[4295322.564000] VFS: Can't find ext3 filesystem on dev sdb.
[4295322.569000] VFS: Can't find an ext2 filesystem on dev sdb.
[4295322.573000] VFS: Can't find an ext2 filesystem on dev sdb.
[4295322.578000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4295322.583000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4295322.587000] XFS: bad magic number
[4295322.587000] XFS: SB validate failed
[4295322.592000] XFS: bad magic number
[4295322.592000] XFS: SB validate failed

I have formatted the USB key with a fat32 file system. 

I have also tried this USB key on my laptop which is also running Ubuntu. No luck there either. 

Any suggestions for getting this working?

Thanks,

Scott

---

### Post by skjantzen on 2006-02-26
I'd sure appreciate some help with this problem.

Thanks,

Scott

---

### Post by skjantzen on 2006-02-28
Is anybody else struggling with their USB  keys not working properly with Ubuntu?

SJ

---

### Post by jasonm on 2008-01-09
i have the same problem.

i have mult computers running ubuntu, some of my usb keys have this problem and others do not.

---

