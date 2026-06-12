---
title: "Brother MFC210C card reader freeze"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by colossus73 on 2007-12-20
Hi,

I have a DCP-115C printer. After a while I accessed the sd card with any program the processes freeze:

gt[~]$ ps ax | grep D
  PID TTY      STAT   TIME COMMAND
 2547 ?        D<     0:00 [scsi_eh_7]
 2548 ?        D<     0:00 [usb-storage]
 5346 ?        D      0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)

and I can't kill them anymore even with sudo. I'm forced to reboot the PC. I have this in the logs:

```

[   41.851676] scsi 7:0:0:0: Direct-Access     Brother  DCP-115C         1.00 PQ: 0 ANSI: 2
[   41.871636] sd 7:0:0:0: [sdc] 999936 512-byte hardware sectors (512 MB)
[   41.887622] sd 7:0:0:0: [sdc] Write Protect is off
[   41.887625] sd 7:0:0:0: [sdc] Mode Sense: 1e 00 00 08
[   41.887628] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   41.932578] sd 7:0:0:0: [sdc] 999936 512-byte hardware sectors (512 MB)
[   41.948562] sd 7:0:0:0: [sdc] Write Protect is off
[   41.948565] sd 7:0:0:0: [sdc] Mode Sense: 1e 00 00 08
[   41.948567] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   41.948571]  sdc: sdc1
[   41.982540]  sdc: p1 exceeds device capacity
[   41.989566] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   41.989622] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   42.545440] attempt to access beyond end of device
[   42.545446] sdc: rw=0, want=1000298, limit=999936
[   42.545449] Buffer I/O error on device sdc1, logical block 1000064
[   42.545453] attempt to access beyond end of device

```

This line looks suspicious to me: [   41.982540]  sdc: p1 exceeds device capacity. 
The kernel is: Linux gt-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux. On windoz the card works like a charm so it's not a problem of filesystem.

Please help!

---

### Post by colossus73 on 2008-04-04
Ping? I even tried with kernel 2.6.24, same problem! Is it possible that nobody else has this problem?

---

### Post by schmatzler on 2008-07-06
I have the same problem, but didn't found a solution yet. :(

I thought, it would have something to do with the printer itself, but its working with Billys crappy OS ;)

---

### Post by colossus73 on 2008-07-06
> **schmatzler said:**
> I have the same problem, but didn't found a solution yet. :(

I thought, it would have something to do with the printer itself, but its working with Billys crappy OS ;)

Did you try with kernel 2.25.x?

---

