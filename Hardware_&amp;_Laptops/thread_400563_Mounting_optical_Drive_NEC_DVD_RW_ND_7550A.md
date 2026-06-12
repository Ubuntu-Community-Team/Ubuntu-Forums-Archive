---
title: "Mounting optical Drive NEC DVD RW ND 7550A"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by fululian on 2007-04-03
hi again,

i changed the completely fragged original optical drive of my vaio (it's commonly known, the sony drives just give it up after a few months, you really gotta love vaios in order to take this) with a new, and very stable NEC DVD RW ND 7550A.

this drive is a really stable one. but i do not seem to mount it correctly: if i insert an empty or full dvd or cd, nothing happens. the only way to reach the dvd/cd is to right click the drive, "open", awaiting the failure notice, then "filesystem", "media" and there i go.

this is the message i get when trying to open the drive:

> the chosen storage medium could't be mounted. you may be using a storage medium with a format that is not montable.

when i press "details":

```

mount: block device /dev/hdb is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so
```

dmesg | tail delivers

```
dmesg | tail
[17187042.124000] printk: 12 messages suppressed.
[17187042.124000] Buffer I/O error on device sda, logical block 0
[17187042.124000]  2:0:0:0: rejecting I/O to dead device
[17187042.124000] Buffer I/O error on device sda, logical block 0
[17187042.124000]  unable to read partition table
[17187489.604000] hdb: media error (bad sector): status=0x51 {
DriveReady SeekComplete Error }
[17187489.604000] hdb: media error (bad sector): error=0x34 {
AbortedCommand LastFailedSense=0x03 }
[17187489.604000] ide: failed opcode was: unknown
[17187489.604000] end_request: I/O error, dev hdb, sector 64
[17187489.604000] isofs_fill_super: bread failed, dev=hdb,
iso_blknum=16, block=16
```

is there a way to solve this or work around a little better than i do?

merci

---

