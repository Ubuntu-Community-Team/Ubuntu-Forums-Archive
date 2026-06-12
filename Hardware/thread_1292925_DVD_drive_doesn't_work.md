---
title: "DVD drive doesn't work"
date: 2009-10-16
forum: Hardware
---

### Post by meisterelrond on 2009-10-16
Hi!
I installed ubuntu 9.10b recently and like it so far, unfortunately my SATA-DVD-drives don't work properly. I can open/play CDs, but as soon as I insert a data/movie-DVD the device will disappear from Nautilus and I won't be able to throw out the disk. No reaction from the drive.
I have a P43/ICH10R chipset with SATA drives. Any suggestions?
Kind regards,
meisterelrond

---

### Post by meisterelrond on 2009-10-18
DVD access does work with Intrepid and other Linux distributions. Has anyone else encountered similar problems?

---

### Post by meisterelrond on 2009-10-19
dmesg:

[    4.092558] ata3: SATA max UDMA/133 abar m2048@0xd0321000 port 0xd0321200 irq 27
[    4.420554] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.421430] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100, ATAPI AN
[    4.422839] ata3.00: configured for UDMA/100
[    4.423185] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    4.423224] ata3: irq_stat 0x40000001
[    4.423262] ata3: hard resetting link
[    5.144029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.146325] ata3.00: configured for UDMA/100
[    5.146668] ata3: EH complete

/var/log/messages:

kernel: [    4.092558] ata3: SATA max UDMA/133 abar m2048@0xd0321000 port 0xd0321200 irq 27
kernel: [    4.420554] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
kernel: [    4.421430] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100, ATAPI AN
kernel: [    4.422839] ata3.00: configured for UDMA/100
kernel: [    4.423262] ata3: hard resetting link
kernel: [    5.144029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
kernel: [    5.146325] ata3.00: configured for UDMA/100
kernel: [    5.146668] ata3: EH complete

The other DVD drive says exactly the same.

---

