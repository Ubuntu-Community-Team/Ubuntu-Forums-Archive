---
title: "PRO Duo memory stick on Sony Vaio"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by cid on 2006-01-12
Recently got a a SanDisk PRO Duo memory stick for my PSP. Happily there's also a PRO card reader built into my VAIO. However Ubuntu doesn't seem to know anything about the card reader.

Nothing showed up in /var/log/messages when I plug/unplug it.

Where else might I look?

This is such a niche piece of hardware that I wouldn't be surprised if there just isn't support for it yet. If I were to write the driver (would be my first) where can I start looking for info?

Other info:

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:02:04.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
0000:02:0b.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)








$ lsdev
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:02.0                 1800-1807
0000:00:1d.0                 1820-183f
0000:00:1d.1                 1840-185f
0000:00:1d.2                 1860-187f
0000:00:1f.0                 1000-107f 1180-11bf
0000:00:1f.1                 1810-181f
0000:00:1f.3                 1880-189f
0000:00:1f.5                 18c0-18ff 1c00-1cff
0000:00:1f.6                 2000-207f 2400-24ff
0000:02:08.0                 3000-303f
ACPI                             1010-1015
cascade             4     2
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
e100                           3000-303f
fpu                          00f0-00ff
GPE0_BLK                         1028-102f
i8042                  1 12
i915@pci:0000:00:02.0          9
ide0                     14  01f0-01f7 03f6-03f6   1810-1817
ide1                     15  0170-0177 0376-0376   1818-181f
Intel                          18c0-18ff   1c00-1cff
keyboard                     0060-006f
motherboard                    1000-107f   1180-11bf fe00-fe01 fe10-fe17
PCI                          0cf8-0cff 4000-40ff 4400-44ff
pic1                         0020-0021
pic2                         00a0-00a1
PM1a_CNT_BLK                     1004-1005
PM1a_EVT_BLK                     1000-1003
PM2_CNT_BLK                      1020-1020
PM_TMR                           1008-100b
rtc                       8  0070-0077
Sony                         1080-109f
sonypi                   11
timer                     0
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       1820-183f   1840-185f   1860-187f
vga+                         03c0-03df

---

