---
title: "[SOLVED] SATA problem ?"
date: 2008-10-18
forum: General Help
---

### Post by efeurich on 2008-10-18
Hi there,

I have installed Ubuntu Studio and have some ATA (I geuss this is related to the SATA interface ) error in my kernel log.
26.773343] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 18 12:13:21 Mercurius kernel: [   26.773352] ata1.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
Oct 18 12:13:21 Mercurius kernel: [   26.773353]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
Oct 18 12:13:21 Mercurius kernel: [   26.773354]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Oct 18 12:13:21 Mercurius kernel: [   26.773357] ata1.01: status: { DRDY }
Oct 18 12:13:21 Mercurius kernel: [   30.184874] ata1: soft resetting link
Oct 18 12:13:21 Mercurius kernel: [   30.800089] ata1.00: configured for UDMA/33
Oct 18 12:13:21 Mercurius kernel: [   30.953814] ata1.01: configured for UDMA/66
Oct 18 12:13:21 Mercurius kernel: [   30.953825] ata1: EH complete
Oct 18 12:13:21 Mercurius kernel: [   36.444421] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 18 12:13:21 Mercurius kernel: [   36.444430] ata1.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
Oct 18 12:13:21 Mercurius kernel: [   36.444431]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
Oct 18 12:13:21 Mercurius kernel: [   36.444432]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Oct 18 12:13:21 Mercurius kernel: [   36.444435] ata1.01: status: { DRDY }
Oct 18 12:13:21 Mercurius kernel: [   39.906625] ata1: soft resetting link
Oct 18 12:13:21 Mercurius kernel: [   40.521820] ata1.00: configured for UDMA/33
Oct 18 12:13:21 Mercurius kernel: [   40.675557] ata1.01: configured for UDMA/66
Oct 18 12:13:21 Mercurius kernel: [   40.675568] ata1: EH complete
Oct 18 12:13:21 Mercurius kernel: [   46.166170] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 18 12:13:21 Mercurius kernel: [   46.166179] ata1.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
Oct 18 12:13:21 Mercurius kernel: [   46.166180]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
Oct 18 12:13:21 Mercurius kernel: [   46.166181]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Oct 18 12:13:21 Mercurius kernel: [   46.166183] ata1.01: status: { DRDY }
Oct 18 12:13:21 Mercurius kernel: [   49.577454] ata1: soft resetting link
Oct 18 12:13:21 Mercurius kernel: [   50.192650] ata1.00: configured for UDMA/33
Oct 18 12:13:21 Mercurius kernel: [   50.346388] ata1.01: configured for UDMA/66
Oct 18 12:13:21 Mercurius kernel: [   50.346399] ata1: EH complete
Oct 18 12:13:21 Mercurius kernel: [   55.837001] ata1.01: limiting speed to UDMA/44:PIO4
Oct 18 12:13:21 Mercurius kernel: [   55.837006] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Oct 18 12:13:21 Mercurius kernel: [   55.837013] ata1.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
Oct 18 12:13:21 Mercurius kernel: [   55.837014]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
Oct 18 12:13:21 Mercurius kernel: [   55.837015]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Oct 18 12:13:21 Mercurius kernel: [   55.837017] ata1.01: status: { DRDY }
Oct 18 12:13:21 Mercurius kernel: [   59.299196] ata1: soft resetting link
Oct 18 12:13:21 Mercurius kernel: [   59.914602] ata1.00: configured for UDMA/33
Oct 18 12:13:21 Mercurius kernel: [   60.068138] ata1.01: configured for UDMA/44
Oct 18 12:13:21 Mercurius kernel: [   60.068154] ata1: EH complete

I also have a problem with a dvd burner Plextor px-716A that doesn't seem to be recognized.

Are these two problems related? How can I get rid of the kernel error. I think that is the problem to be fixed first.

Anyone?

Thanks in advanced,

EIF

---

### Post by bDerrly on 2008-10-18
Can you give the output of `sudo sfdisk -l` and `sudo hdparm -t /dev/sd*` (run these in a terminal). My first guess would be a faulty hard drive. Though, it could be a controller on the motherboard if your DVD drive is not being detected.

---

### Post by efeurich on 2008-10-19
Here is the output of sfdisk -l;

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  18661   18662- 149902483+  83  Linux
/dev/sda2      18662   19456     795    6385837+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      18662+  19456     795-   6385806   82  Linux swap / Solaris

Looks pretty normal to me.

Awaiting your response :)

---

