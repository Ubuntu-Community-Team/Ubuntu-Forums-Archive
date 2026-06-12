---
title: "another DMa problem"
date: 2008-07-31
forum: Hardware
---

### Post by oguzy on 2008-07-31
I need help on seeting up my DMA and PIO at mt SATA drive. 

I am using Hardy. 

# dmesg | grep DMA
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   18.501321] ata1: SATA max UDMA/133 abar m2048@0x38404000 port 0x38404100 irq 219
[   18.501325] ata2: SATA max UDMA/133 abar m2048@0x38404000 port 0x38404180 irq 219
[   18.501328] ata3: SATA max UDMA/133 abar m2048@0x38404000 port 0x38404200 irq 219
[   18.878170] ata1.00: ATA-7: WDC WD800BEVS-07RST0, 04.01G04, max UDMA/133
[   18.879906] ata1.00: configured for UDMA/133
[   18.979830] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x60e0 irq 14
[   18.979833] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60e8 irq 15
[   19.313601] ata4.00: ATAPI: TSSTcorpCDW/DVD SN-M242D, SB00a, max UDMA/33
[   19.516432] ata4.00: configured for UDMA/33

# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#manuel
sd_mod
psmouse
mousedev
piix
ide-core
ide-cd
ide-disk
ide-generic
#manuel

fuse
lp
sbp2
uinput
acpi-cpufreq
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace

lsmod: [http://pastebin.com/f2367af13](http://pastebin.com/f2367af13)

# hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD800BEVS-07RST0                    , FwRev=04.01G04, SerialNo=     WD-WXC507001547
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

# hdparm -X udma5 /dev/sda

/dev/sda:
 setting xfermode to 69 (UltraDMA mode5)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error

So how can i fix it?

---

