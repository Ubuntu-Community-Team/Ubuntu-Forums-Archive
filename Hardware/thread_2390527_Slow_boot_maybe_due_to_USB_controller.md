---
title: "Slow boot maybe due to USB controller"
date: 2018-04-29
forum: Hardware
---

### Post by rzrbny on 2018-04-29
Just installed Ubuntu 18.04 and I'm having some problems with long boot times on an ssd, boot takes roughly 30 secs. From what I've gathered there seems to be a problem with my USB controller. I'm using a rather old motherboard Gibayte z77x-ud3h.

Part of my dmesg is

```

[    7.265240] usb 3-4: Manufacturer: SteelSeries
[   29.694444] xhci_hcd 0000:03:00.0: can't setup: -110
[   29.694454] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x3280bbc86a3, max_idle_ns: 440795343760 ns
[   29.694456] xhci_hcd 0000:03:00.0: USB bus 5 deregistered
[   29.694496] xhci_hcd 0000:03:00.0: init 0000:03:00.0 fail, -110
```
and according to lspci this device is my USB controller

```

03:00.0 USB controller: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller (rev 03)
```

Any suggestions to solving this problem? New to linux and ubuntu so don't really know what I'm doing.

---

### Post by junaidahmed2 on 2018-04-29
A large number of people are experiencing slow boot issue after installing xUbuntu 18.04.

---

### Post by rzrbny on 2018-04-30
I forgot to mention i experienced the same slow boot using 17.10.1 last week but I didn't pursue the problem then.

---

