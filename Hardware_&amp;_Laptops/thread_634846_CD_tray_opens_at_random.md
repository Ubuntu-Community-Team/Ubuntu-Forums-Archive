---
title: "CD tray opens at random"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by eggdeng on 2007-12-08
The CD / DVD tray on my Gericom X5 Force laptop opens at random when not in use. I am using a 2.6.17-12-generic kernel on 6.10.

Drive info from lshw is as follows:

```
cdrom
                   description: DVD reader
                   product: QSI CD-RW/DVD-ROM SBW-161
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: SX09
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
```

The entry in /etc/fstab is

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0 
```

dmesg | tail gives

```

[17180051.736000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180051.780000] ISO 9660 Extensions: RRIP_1991A
[17180175.300000] hdc: irq timeout: status=0xd0 { Busy }
[17180175.300000] ide: failed opcode was: unknown
[17180175.300000] hdc: DMA disabled
[17180205.300000] hdc: ATAPI reset timed-out, status=0xd0
[17180235.300000] ide1: reset timed-out, status=0x90
[17180240.304000] hdc: status timeout: status=0x90 { Busy }
[17180240.304000] ide: failed opcode was: unknown
[17180240.304000] hdc: drive not ready for command
[17180255.668000] hdc: ATAPI reset complete
```

Any ideas appreciated.

---

### Post by MidianLies on 2007-12-19
Damn, stuff really just goes completely without response. I guess my post is out of luck as well.

---

### Post by eggdeng on 2007-12-19
In my case, it turned out to be a hardware problem. The box in question has a W*nd*ws partition and the same problem occurs there. I hadn't noticed earlier as no-one ever boots  W*nd*ws.

---

