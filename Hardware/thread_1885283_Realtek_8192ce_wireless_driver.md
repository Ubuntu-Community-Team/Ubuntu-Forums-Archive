---
title: "Realtek 8192ce wireless driver"
date: 2011-11-22
forum: Hardware
---

### Post by attilitus on 2011-11-22
My driver for my rtl8192ce wireless minipci card is very unstable in Ubuntu. (frequent disconnects and slow connection)

lspci -v output:

```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8195
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 5000 [size=256]
	Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce
```

In windows the driver used is for RTL8192ce.

I've spent quite a bit of time trying to solve the issue. Here are a few things I've noticed:

The actual card says 'rev 02' instead of 'rev 01' as listed in output of lspci.

This bug seems to describe my problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871/comments/5)

Any help would be appreciated (please let me know of any commands I can run to get more information). Card works perfectly in windows.

---

### Post by wolfen69 on 2011-11-23
Which version of ubuntu are you using?

---

