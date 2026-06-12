---
title: "Laptop Hard Drive -- Lots of I/O Wait"
date: 2008-05-10
forum: Hardware
---

### Post by craigp84 on 2008-05-10
Hi Guys,

I'm running hardy on a PowerBook G4, with a ATA/ATAPI-6 harddrive in udma5 mode (using DMA). This is set up for me on boot automatically, which is nice :).

I have a process which does *lots* of disk reading, currently it takes > 1hr to run. I'd like to bring this down a bit.

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          13.00    0.00    8.00   79.00    0.00    0.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
hda             134.00      2744.00         0.00       2744          0

```

As you can see, the CPU's sitting idle when it could be processing the data, if i could just get more data off the disk faster.

I'm **peaking at around 3MB/sec read rate**. Seems a bit slow.

I've tried various settings through hdparm for I/O mult sect (0 up to 16) but lower numbers seem to work best which wasn't what i was expecting. The man page suggests this is the case for some WesternDigital drives, mines is a Fuujitsu. Oh well :confused:

Also tried upping the readahead from 256 to 512, but if anything it was lower throughput.

I also put the PCI side into 32 bit (with sync bit), and it did make a very small improvement.

Having exhausted hdparm, and confirmed that there's no shortcuts i can take on the application side (i.e. it must read all this data), i'm pretty much stuck :-(

Any ideas greatly appreciated!

-c

---

