---
title: "Windows 7 burned disc not recognised"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by kranny on 2009-01-17
I have burned a data Dvd using the Dvd writer that comes with windows 7 on my friend's system...I can se the contents in Windows 7 but hardy couldnt recognise it..Anyone faced the same....

dmesg|tail gives
```
[  566.400533] cdrom: This disc doesn't have any tracks I recognize!
[ 1182.526007] attempt to access beyond end of device
[ 1182.526018] hdb: rw=0, want=68, limit=4
[ 1182.526521] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
[ 1953.592617] kjournald starting.  Commit interval 5 seconds
[ 1953.593146] EXT3 FS on sda11, internal journal
[ 1953.593155] EXT3-fs: mounted filesystem with ordered data mode.
[ 2267.661882] cdrom: This disc doesn't have any tracks I recognize!
```

---

