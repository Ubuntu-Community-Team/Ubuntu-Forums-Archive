---
title: "Slow boot time on Toshiba L750"
date: 2012-06-21
forum: Hardware
---

### Post by qwe2 on 2012-06-21
I use Ubuntu 12.04 x64 alongside a Windows 7. Booting ubuntu takes too much time in my opinon. It's no big deal but it's a bit annoying that my windows starts 3-4 times faster than my ubuntu.

I checked dmesg  but it doesn't really tell me anything on what the problem could be as I'm pretty new to linux systems but I think the problem should be here:

```
[    9.887209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.890712] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.895411] atl1c 0000:0a:00.0: irq 52 for MSI/MSI-X
[    9.979727] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.981211] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.574543] wlan0: authenticate with 00:1f:1f:30:7d:5c (try 1)
[   12.577740] wlan0: authenticated
[   12.607078] wlan0: associate with 00:1f:1f:30:7d:5c (try 1)
[   12.611223] wlan0: RX AssocResp from 00:1f:1f:30:7d:5c (capab=0xc11 status=0 aid=2)
[   12.611233] wlan0: associated
[   12.618079] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.598937] Bluetooth: Can't change to loading configuration err
[   13.598966] ath3k: probe of 1-1.6:1.0 failed with error -110
[   13.599018] usbcore: registered new interface driver ath3k
[   23.823661] wlan0: no IPv6 routers present
[   69.748458] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.VGA_.LCD_.NINT] (Node ffff88024185c870), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[   69.748468] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.VGA_.LCD_._BCM] (Node ffff88024185c8e8), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[   69.748476] ACPI Error: Evaluating _BCM failed (20110623/video-372)
[   69.748552] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2f/LNXVIDEO:00/input/input13
[   69.748603] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   69.948864] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   69.948867] vesafb: scrolling: redraw
[   69.948870] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   69.953525] vesafb: framebuffer at 0xc1000000, mapped to 0xffffc90011b80000, using 1216k, total 1216k
[   69.953629] Console: switching to colour frame buffer device 80x30
[   69.953639] fb0: VESA VGA frame buffer device
[   69.981253] init: plymouth-splash main process (1275) terminated with status 1
``` So if anyone could give me an answer or just a hint that would be greatly appreciated.

---

### Post by qwe2 on 2012-06-27
Made a bootchart if that helps anybody.

[http://i.imgur.com/0Sp6d.png](http://i.imgur.com/0Sp6d.png)

---

### Post by qwe2 on 2012-06-29
3.40 BIOS update solved it.

---

