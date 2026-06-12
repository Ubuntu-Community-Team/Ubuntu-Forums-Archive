---
title: "Notebook hangs out"
date: 2012-05-13
forum: Hardware
---

### Post by erbedo on 2012-05-13
Hi
    I noticed that, from time to time, my notebook hangs out for about 10/20 seconds, and after that continues to work fine.
After one of this hangs, this is the output of dmesg:
```

[ 8312.195009] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 8312.195012] ata1.00: irq_stat 0x40000008
[ 8312.195014] ata1.00: failed command: READ FPDMA QUEUED
[ 8312.195018] ata1.00: cmd 60/08:00:55:44:84/00:00:30:00:00/40 tag 0 ncq 4096 in
[ 8312.195019]          res 41/40:08:5c:44:84/00:00:30:00:00/00 Emask 0x409 (media error) <F>
[ 8312.195021] ata1.00: status: { DRDY ERR }
[ 8312.195022] ata1.00: error: { UNC }
[ 8312.268159] ata1.00: configured for UDMA/133
[ 8312.268191] sd 0:0:0:0: [sda] Unhandled sense code
[ 8312.268196] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8312.268204] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[ 8312.268214] Descriptor sense data with sense descriptors (in hex):
[ 8312.268218]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 8312.268238]         30 84 44 5c 
[ 8312.268246] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 8312.268256] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 30 84 44 55 00 00 08 00
[ 8312.268283] end_request: I/O error, dev sda, sector 813974620
[ 8312.268300] ata1: EH complete

```

Maybe it's related. If it is, any idea on how to solve this?

Thanks

---

### Post by moshuptrail on 2012-09-02
Did you get NO responses?  Used to be someone would always jump on.

I get the same error and have the same behavior (long pauses when I start an app) from my laptop.  I suspect the HD is going bad and has some bad sectors.  That is what the error would seem to indicate.

What I don't know, and perhaps someone in the Linux community can tell us, is how good is Linux at isolating bad sectors so they don't get used and what utilities might be run to do that?

Does it depend on the disk format?

---

### Post by 2F4U on 2012-09-02
Looks to me as if there is at least one bad sector on the hdd:

```
[ 8312.268283] end_request: I/O error, dev sda, sector 813974620
```

It may be a good idea to see if there are more errors. The disk utility usually has some S.M.A.R.T. data that may have more details.

---

### Post by kimberlite on 2012-09-02
> **2F4U said:**
> 
It may be a good idea to see if there are more errors. The disk utility usually has some S.M.A.R.T. data that may have more details.

+1 Run disk utility on Ubuntu 11.10+ and gnome3/unity DE: press super and type "disk utility", than press "SMART Data/view SMART data" button. There you may want to run a self-test on your sda disk.

---

### Post by moshuptrail on 2012-09-23
Cool Utility.  Had no idea about that.
It is showing 2 bad sectors.  And no sectors already re-allocated.
However, it's also showing a warning: #197, Current Pending Sector Count
For some reason it's not reallocating these secotors.  Can I force it?

---

### Post by Erik1984 on 2012-09-24
I have the same problem for a while now in different versions of *buntu, it happened today and finally decided to run the Western Digital diagnostics tool (a dedicated tool by WD on a CD that is OS agnostic)... took 2 hours to scan the disk and reported no single error. Not sure this is a hardware problem. Seems to be a general Linux issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)

---

