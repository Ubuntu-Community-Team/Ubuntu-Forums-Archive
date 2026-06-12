---
title: "PCIe SATA card not recognizing drives"
date: 2014-08-23
forum: Hardware
---

### Post by BaridBelMedar on 2014-08-23
I have 1 SYBA SD-PEX50055 card with 2 hard drives connected and another with a dvd drive. The drives all show up in the bios, but none of them show up once linux is loaded. When I boot linux, the sata controllers are loaded as 04:00.0 and 0a:00.0, but the hard drives and the dvd drive don't show up in /dev as block devices.


uname -a
```
Linux [redacted] 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

lspci | grep 04:00.0

```
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
```

dmesp | grep 04:00.0
```
[    0.412031] pci 0000:04:00.0: [1b21:0612] type 00 class 0x010601
[    0.412045] pci 0000:04:00.0: reg 0x10: [io  0xd050-0xd057]
[    0.412055] pci 0000:04:00.0: reg 0x14: [io  0xd040-0xd043]
[    0.412064] pci 0000:04:00.0: reg 0x18: [io  0xd030-0xd037]
[    0.412074] pci 0000:04:00.0: reg 0x1c: [io  0xd020-0xd023]
[    0.412084] pci 0000:04:00.0: reg 0x20: [io  0xd000-0xd01f]
[    0.412094] pci 0000:04:00.0: reg 0x24: [mem 0xfe410000-0xfe4101ff]
[    0.412104] pci 0000:04:00.0: reg 0x30: [mem 0xfe400000-0xfe40ffff pref]
[   19.435928] ahci 0000:04:00.0: irq 79 for MSI/MSI-X
[   19.436139] ahci 0000:04:00.0: SSS flag set, parallel bus scan disabled
[   19.436168] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[   19.436171] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs
```

---

### Post by MartyBuntu on 2014-08-25
Are the drives formatted yet?

Do they show up in GParted?

---

### Post by mark206 on 2015-03-19
Hey I am new to this forum and relativity new to Ubuntu. I seem to have the same issue. I installed a SYBA SI-PEX40064 PCI-Express 2.0 Low Profile Ready SATA III (6.0Gb/s) Controller Card and connected two drives but fdisk isn't recognizing them. I made sure that ACHI is selected in the BIOS. The drives have been formatted and they are recognized when directly plugged into the motherboard.

uname –a
```

Linux XXXXXXX 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux

```
lspci | grep 00:1f.2
```

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 04)

```
dmesg | grep 00:1f.2
```

[    0.200952] pci 0000:00:1f.2: [8086:1c02] type 00 class 0x010601
[    0.200970] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.200977] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.200985] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.200993] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.201001] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.201009] pci 0000:00:1f.2: reg 0x24: [mem 0xf7c06000-0xf7c067ff]
[    0.201053] pci 0000:00:1f.2: PME# supported from D3hot
[    1.254076] ahci 0000:00:1f.2: version 3.0
[    1.254197] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.254224] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.269992] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.269996] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst

```
fdisk -l (There are three disks connected directly which are shown below, and two disks connected to the PCIe which are not recognized) 
```


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d9608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953523711   976760832   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f0501

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1953523711   976760832   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00035106

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux

Disk /dev/sdd: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   312498175   156248064   83  Linux

Disk /dev/md0: 1000.1 GB, 1000068349952 bytes
255 heads, 63 sectors/track, 121584 cylinders, total 1953258496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 524288 bytes
Disk identifier: 0x00059c99

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1            1024  1945076735   972537856   83  Linux
/dev/md0p2      1945077758  1953257471     4089857    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/md0p5      1945077760  1953257471     4089856   82  Linux swap / Solaris

```

I have been working on this for the past few days with no success. I would really appreciate any thoughts. Thanks a lot.

---

