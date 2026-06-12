---
title: "Weird problem with Verbatim USB stick"
date: 2016-10-16
forum: Hardware
---

### Post by Chalisque on 2016-10-16
This one has me scratching my head. I bought two (for cheap price) Verbatim 64GB 'store n go' sticks. One of them works fine on Linux, the other does not. The second one (the one with problems), tried on two separate machines running Ubuntu 16.04 LTS, fails to read properly. I managed to create an exfat partition, but attempting a raw read from the device with dd just yielded a file full of 'ff ff ff ff' strings (that is, all bits 1). Putting the stick into a Windows machine, or a mac, it appears to read fine. This has been tried on two Acer machines running Ubuntu 16.04 so far. 

I am wondering as to thoughts as to how to figure out what is going on? 

(I just have a job running on the Windows box filling it with files, so that I can see which machines can and cannot read this stick, but it is an odd one.)

uname yields: 

```
Linux $HOSTNAME 4.4.0-38-lowlatency #57-Ubuntu SMP PREEMPT Tue Sep 6 16:59:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

dmesg yields (upon plugging in):
```
[  474.856755] scsi 6:0:0:0: Direct-Access     Verbatim STORE N GO       8.07 PQ: 0 ANSI: 4
[  474.857764] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  474.859714] sd 6:0:0:0: [sdc] 122880000 512-byte logical blocks: (62.9 GB/58.6 GiB)
[  474.860854] sd 6:0:0:0: [sdc] Write Protect is off
[  474.860865] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  474.861963] sd 6:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  474.870585]  sdc: sdc1
[  474.874376] sd 6:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by ajgreeny on 2016-10-16
Do you have the **exfat-fuse** and **exfat-utils** packages needed installed in your Ubuntu system.

What did you use the create the exfat partitions?

---

