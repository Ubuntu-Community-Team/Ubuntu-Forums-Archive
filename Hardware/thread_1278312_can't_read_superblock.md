---
title: "can't read superblock"
date: 2009-09-29
forum: Hardware
---

### Post by starfleetcaptainrob on 2009-09-29
Hello, I have an external hard drive that I have hooked up via an eSata/Sata crossover cable.  Noticed last night when I went to access the drive that several of the folders were missing.  So I umounted the drive and when I went to remount it I got this:

```
mount: /dev/sdb1: can't read superblock
```

A sudo fsck -t vfat /dev/sdb1 command returns this:

```
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
Read 512 bytes at 0:Input/output error

```

sudo dmesg | tail returns the following:

```
[205858.619237] Buffer I/O error on device sdb1, logical block 2
[205858.619240] Buffer I/O error on device sdb1, logical block 3
[205858.619244] Buffer I/O error on device sdb1, logical block 4
[205858.619247] Buffer I/O error on device sdb1, logical block 5
[205858.619250] Buffer I/O error on device sdb1, logical block 6
[205858.619252] Buffer I/O error on device sdb1, logical block 7
[205858.619255] Buffer I/O error on device sdb1, logical block 8
[205858.619258] Buffer I/O error on device sdb1, logical block 9
[205858.619290] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[205858.619294] end_request: I/O error, dev sdb, sector 63

```

So is my drive completely gone?

---

### Post by starfleetcaptainrob on 2009-09-29
Reboot took care of everything.  Thanks!

---

