---
title: "STG4000 [3D Prophet Kyro Series]"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by redchuck on 2009-05-13
I realize this is an ancient card and support is unlikely, but what the heck.

I have a PCI GC-K2P-64 Pixel Perfect video card that comes up in 800x600 mode.  Is it possible to get better resolution than this on Jaunty?

```

$ sudo lshw -c video
       description: VGA compatible controller
       product: STG4000 [3D Prophet Kyro Series]
       vendor: STMicroelectronics
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 0f
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=64
$ sudo lspci -v
04:00.0 VGA compatible controller: STMicroelectronics STG4000 [3D Prophet Kyro Series] (rev 0f)
	Subsystem: STMicroelectronics Device 4990
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at f8000000 (32-bit, prefetchable) [size=512K]
	I/O ports at dc00 [size=256]
	Expansion ROM at f8080000 [disabled] [size=128K]
	Capabilities: [40] AGP version 2.0
	Capabilities: [60] Power Management version 2
	Kernel modules: kyrofb


```


The best advice I've found so far is to bag it up and send it to a museum, as drivers haven't been available since Linux 2.4.

[http://test.ubuntuforums.org/showthread.php?t=205377](http://test.ubuntuforums.org/showthread.php?t=205377)

[http://klt.sourceforge.net/](http://klt.sourceforge.net/)

Any help? :-D

---

