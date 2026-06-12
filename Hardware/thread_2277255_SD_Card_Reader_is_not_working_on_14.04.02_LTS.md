---
title: "SD Card Reader is not working on 14.04.02 LTS"
date: 2015-05-07
forum: Hardware
---

### Post by canavaroski90 on 2015-05-07
Hi all,

On boot integrated sd card reader on my laptop works charmless but after some time it stops responding and does not detect any card attached. If I remove driver via 

```
rmmod rts5208
```

and reload it via
```
modprobe rts5208
```

sometimes it works. But generally it continues to fail situation.

doing rescan for pcie devices is not helped also.

```
[COLOR=#111111][FONT=Consolas]echo 1 | sudo tee /sys/bus/pci/rescan[/FONT][/COLOR]
```

lspci output:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0d:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
19:00.0 USB controller: Fresco Logic FL1009 USB 3.0 Host Controller (rev 02)
```

some dmesg output relevant to sd card controller ( after >>> symbol my own comments reside)

```
[ 6897.344805] mmc1: card aaaa removed  >>> occurs when sd card detached 
[ 6968.627770] mmc1: cannot verify signal voltage switch  >>> occurs when sd card attached 
[ 6968.742355] mmc1: new ultra high speed SDR50 SDHC card at address aaaa  >>> occurs when sd card attached 
[ 6968.742504] mmcblk0: mmc1:aaaa SL08G 7.40 GiB     >>> occurs when sd card attached
[ 6968.752928]  mmcblk0: p1   >>> occurs when sd card attached
[ 8824.085591] mmc1: card aaaa removed   >>> occurs when sd card detached 
[ 8912.940350] rts5208: rtsx_exit() called    >>> occurs on rrmod rts5208
[ 8912.940389] rts5208: rts5208 module exit    >>> occurs on rrmod rts5208
[ 8930.043320] rts5208: module is from the staging directory, the quality is unknown, you have been warned.     >>> occurs on modprobe rts5208
[ 8930.044609] rts5208: Initializing Realtek PCIE storage driver...     >>> occurs on modprobe rts5208

```


any idea?

---

