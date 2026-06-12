---
title: "Looking for high(er) performance RAID solution"
date: 2017-03-10
forum: Hardware
---

### Post by ltburch2000 on 2017-03-10
I currently have a mediasonic 8bay ESATA storage box with a 6 3TB WD Red drives in MDADM RAID6 configuration.  Unfortunately the performance is generally lacking even on read(I expected poor write performance).  I only can copy off the RAID at about 35MB/sec,  if I run a check array it reads from the drives at  only 15-22mb/sec (takes about 2 days to run a checkarray).  Space is also filling up.

So I am looking for higher capacity along  with faster read/write/check speeds.  First off, I plan to switch to ZFS, which seems more feature rich and higher performance than MDADM.  But I also wonder hardware wise is there any reasonably affordable alternative to an ESATA storage box for a 5+ 8TB drive array.  I would like to be able to see the drives run at least in read at or near their full speed of  150MB/sec or so (x 5-6  for the raid).  Is the only alternatives things like enterprise SANs beyond simple ESATA?  Is it perhaps a low performance ESATA card holding me back?

---

### Post by TheFu on 2017-03-11
I'd look at your eSATA controller.  If you want high RAID performance, you'll need a true HW-RAID card - probably from LSI and probably in the SAS line running around US$350.  Using HW-RAID causes some other limitations. Your storage will be tied to that specific card and you'll want to buy a spare for when it fails. Replacements bought 3 yrs later may have a different internal storage setup and be incompatible.  SW-RAID is really convenient when you need HA.

Of course, RAID doesn't prevent the need to have excellent backups. When RAID goes bad, sometimes the only solution is to rebuild it and restore from backups.

I've read on NAS-4-Free that a specific Supermicro JBOD card is popular with ZFS people. It isn't a RAID card, but for ZFS, a RAID card isn't needed.
"Supermicro AOC-SAS2LP-MV8 Add-on Card, 8-Channel SAS/SATA Adapter with 600MB/s per Channel"  US$110 on amazon. You'll need some SAS-to-SATA cables too.

---

### Post by ltburch2000 on 2017-03-11
Thanks, that sounds like just the sort of thing I am looking for.

---

