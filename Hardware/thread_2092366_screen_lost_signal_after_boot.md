---
title: "screen lost signal after boot"
date: 2012-12-07
forum: Hardware
---

### Post by lkthomas on 2012-12-07
my ubuntu just reinstall from scratch.


Detail:

 lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1e.0 SD Host controller: Intel Corporation System Controller Hub (SCH Poulsbo) SDIO Controller #1 (rev 07)
00:1e.1 SD Host controller: Intel Corporation System Controller Hub (SCH Poulsbo) SDIO Controller #2 (rev 07)
00:1e.2 SD Host controller: Intel Corporation System Controller Hub (SCH Poulsbo) SDIO Controller #3 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
root@thomas-home:/mnt/etc/network# uname -a
Linux thomas-home 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686 i686 i686 GNU/Linux
_________________

/var/log/syslog

[    1.537701] [drm] Initialized drm 1.1.0 20060810
[    1.554517] gma500 0000:00:02.0: setting latency timer to 64
[    1.586082] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.586542] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.586768] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input3
[    1.587076] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.587084] [drm] No driver support for vblank timestamp query.
[    1.611380] sdhci: Secure Digital Host Controller Interface driver
[    1.611389] sdhci: Copyright(c) Pierre Ossman
[    1.969721] Raw EDID:
[    1.969731]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969735]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969739]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969743]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969746]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969750]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969754]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969757]          00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    1.969768] gma500 0000:00:02.0: LVDS-1: EDID block 0 invalid.
[    2.506642] gma500 0000:00:02.0: Backlight lvds set brightness 7a120000
[    2.506668] [drm] Initialized gma500 1.0.0 2011-06-06 for 0000:00:02.0 on minor 0


___________


problem:

whenever I machine boot up, screen lost signal.

Anyone have idea why?

---

