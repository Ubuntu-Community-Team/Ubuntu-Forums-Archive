---
title: "which graphics card is in use?"
date: 2015-12-28
forum: Hardware
---

### Post by pkoukoulis-r on 2015-12-28
Hi

shows 2 graphics cards, but which one is really being used??

```
$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
	Subsystem: CLEVO/KAPOK Computer Device [1558:5281]
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
	Subsystem: CLEVO/KAPOK Computer Device [1558:5281]
	Flags: bus master, fast devsel, latency 0, IRQ 39
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104M [GeForce GTX 880M] [10de:1198] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: CLEVO/KAPOK Computer Device [1558:5281]
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
	Subsystem: CLEVO/KAPOK Computer Device [1558:5281]
```

---

### Post by efflandt on 2015-12-28
On my MSI laptop, my power LED tells me which graphics is in use. The LED is cool [COLOR=#0000ff]blue[/COLOR] when using the lower power slower Intel graphics, and [COLOR=#ff8c00]amber[/COLOR] when using the faster hotter Nvidia graphics (GTX 765M in my case). But I do not even know how to switch to Nvidia graphics when using the default nouveau driver. If you install a suitable nvidia driver package, it includes nvidia-prime and you can select which graphics is being used from **NVIDIA X Server Settings**. Although, it is not instant. When switching Nvidia to Intel I have to log out of X and back in. When switching from Intel to Nvidia I have to reboot.

Another way to switch graphics is by using bumblebee, which can switch graphics on the fly by using "optirun " or "primusrun " prefix to run a program or game. But it is sort of a cobble, because it relays the Nvidia graphics through the Intel graphics for display which is not as fast as using Nvidia graphics directly. And using optirun for Steam Source games required additional parameters. So I have not used that since (now obsolete) Ubuntu 13.10 when bumblebee was the only way (and I never could get primusrun to work for anything).

---

