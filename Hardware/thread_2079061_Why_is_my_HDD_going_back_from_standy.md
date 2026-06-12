---
title: "Why is my HDD going back from standy?"
date: 2012-11-01
forum: Hardware
---

### Post by armkbdotcom on 2012-11-01
My hard drives, connected to Ubuntu server are producing the following log every exactly 5 minutes.

```
    Nov  1 14:10:50 localhost kernel: [ 1602.884936] ata2.00: hard resetting link
    Nov  1 14:10:51 localhost kernel: [ 1603.226804] ata2.01: hard resetting link
    Nov  1 14:10:52 localhost kernel: [ 1604.274533] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
    Nov  1 14:10:52 localhost kernel: [ 1604.274548] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
    Nov  1 14:10:52 localhost kernel: [ 1604.356669] ata2.00: configured for UDMA/133
    Nov  1 14:10:52 localhost kernel: [ 1604.375247] ata2.01: configured for UDMA/133
    Nov  1 14:10:52 localhost kernel: [ 1604.375265] ata2: EH complete
```

I don't think this is related to hard drive failure, because it happens for ALL hard drives connected and ONLY when I write 
    
    **spindown_time = 12**

in `/etc/hdparm.conf`. The reason I add this value is to put disks into standby mode after 60 seconds, which is happening after that period (checked with hdparm -C).

The first clue I thought that smartd was running and spinning the drive. However, I couldn't find it in `ps -aux | grep smart`. 

Additionally, iostat does show that nobody accessed those drives, since Blk_read, Blk_wrtn remain unchanged. I also killed all processes that may be doing something with hdd(eg SAMBA). So I guess the problem is solely with hdparm...

I have no more clue where that 5 minute value hides.

---

