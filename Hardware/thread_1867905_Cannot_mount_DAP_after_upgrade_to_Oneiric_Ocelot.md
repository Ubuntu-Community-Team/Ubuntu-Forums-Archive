---
title: "Cannot mount DAP after upgrade to Oneiric Ocelot"
date: 2011-10-23
forum: Hardware
---

### Post by kallek on 2011-10-23
Hi,

I got a digital audio player (iriver E 300) that used to nicely mount and be read/writable to from two different Ubuntu computers. But, since upgrading to Oneiric Ocelot a few days ago it is no longer possible. The device doesn't show up in Nautilus.

dmesg gives the following output:
```
~$ dmesg | tail
[94971.712512] scsi 6:0:0:1: Direct-Access     iriver   E300             0100 PQ: 0 ANSI: 0 CCS
[94971.727372] sd 6:0:0:0: Attached scsi generic sg2 type 0
[94971.727843] sd 6:0:0:1: Attached scsi generic sg3 type 0
[94971.734710] sd 6:0:0:0: [sdb] 7393280 512-byte logical blocks: (3.78 GB/3.52 GiB)
[94971.736574] sd 6:0:0:0: [sdb] Write Protect is off
[94971.736583] sd 6:0:0:0: [sdb] Mode Sense: 00 12 00 00
[94971.738060] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[94971.739045] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[94971.745076]  sdb:
[94971.749441] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

Both computers have the same problem and dmesg give the same output. However, I'm not quite certain whether the problem arose right at the upgrade to Oneiric or at an update a few days later.
The DAP is accessible from a mac, so I do not believe the it's broken.

Kernel version:
```
 uname -a
Linux tizoc 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
```

Any advice? Should I post this as a bug?

---

### Post by kallek on 2011-10-24
I tried booting an earlier kernel, but it didn't help.
```
uname -a
Linux Xitlali 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

However, the dmesg output looks different. To me it looks like it should be accessible. But, still, I cannot see it in nautilus.
```

[  382.830085] usb 1-7: new high speed USB device using ehci_hcd and address 8
[  384.620256] hub 1-0:1.0: unable to enumerate USB device on port 7
[  389.060038] usb 1-7: new high speed USB device using ehci_hcd and address 9
[  389.214543] scsi8 : usb-storage 1-7:1.0
[  390.257298] scsi 8:0:0:0: Direct-Access     iriver   E300             0100 PQ: 0 ANSI: 0 CCS
[  390.258023] scsi 8:0:0:1: Direct-Access     iriver   E300             0100 PQ: 0 ANSI: 0 CCS
[  390.260585] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  390.260963] sd 8:0:0:1: Attached scsi generic sg4 type 0
[  390.270147] sd 8:0:0:0: [sdc] 7393280 512-byte logical blocks: (3.78 GB/3.52 GiB)
[  390.272650] sd 8:0:0:0: [sdc] Write Protect is off
[  390.272655] sd 8:0:0:0: [sdc] Mode Sense: 00 12 00 00
[  390.272659] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  390.273161] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[  390.276021] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  390.277665]  sdc:
[  390.281154] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  390.281161] sd 8:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by kallek on 2012-04-05
After the last kernel update it works fine again.

---

