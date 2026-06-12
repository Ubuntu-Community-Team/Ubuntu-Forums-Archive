---
title: "USB external disk passes to read only"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by moky on 2008-01-10
**This post could be related to an Ubuntu bug filed at**: lo [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello


   I have my home directory on an external USB disk drive. It is formated as ext3.
   My problem is that it passes sometimes to read-only mode. Why ? It mostly happens when I do not use my compute during 10 minutes.

  How to mount sdb3 to /home in such a way that it remains read and write even if I do not use it for hours ?
  By the way, I have no problem when a movie is running. Thus I suppose it is a matter of using the disk ...

Any ideas ?

In fstab :
# /dev/sdb3
UUID=9b67edf4-1f07-4188-8543-d6e5f61638ee /home           ext3    defaults        0       2



Best
Laurent

---

### Post by moky on 2008-01-11
I can give an information complement. Here is the dmesg right after passing in read only mode

[   47.746308] Bluetooth: RFCOMM TTY layer initialized
[   47.746312] Bluetooth: RFCOMM ver 1.8
[   52.026441] NET: Registered protocol family 17
[   72.847815] eth0: no IPv6 routers present
[ 9479.922279] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]
[ 9479.922290] : Add. Sense: Logical unit not ready, initializing command required
[ 9479.922299] end_request: I/O error, dev sdb, sector 58402903
[ 9479.926779] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]
[ 9479.926789] : Add. Sense: Logical unit not ready, initializing command required
[ 9479.926798] end_request: I/O error, dev sdb, sector 58402919
[ 9479.926804] Buffer I/O error on device sdb3, logical block 24928
[ 9479.926808] lost page write due to I/O error on sdb3
[ 9479.926823] Aborting journal on device sdb3.
[ 9482.124692] ext3_abort called.
[ 9482.124700] EXT3-fs error (device sdb3): ext3_journal_start_sb: Detected aborted journal
[ 9482.124706] Remounting filesystem read-only
[ 9487.130050] sd 5:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]
[ 9487.130059] : Add. Sense: Logical unit not ready, initializing command required
[ 9487.130068] end_request: I/O error, dev sdb, sector 52895952
[ 9487.130074] Buffer I/O error on device sdb2, logical block 2949174
[ 9487.130078] lost page write due to I/O error on sdb2

I conclude I have some errors on my filesystem. I'll check for badblocks.

Any other ideas ?

Tanks
Laurent

---

