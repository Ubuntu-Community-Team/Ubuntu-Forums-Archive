---
title: "Status of Video Chipset"
date: 2011-10-04
forum: Hardware
---

### Post by Inkit on 2011-10-04
My HP tm2t system has got two video chipsets. ATI and Intel one. As the heat consumption is too much I believe both the chipset are "On".

The output of "lspci -v" has got :

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 3661
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 40f0 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
```

```
01:00.0 VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]
	Subsystem: Hewlett-Packard Company Device 3661
	Flags: fast devsel, IRQ 11
	Memory at c0000000 (32-bit, prefetchable) [disabled] [size=256M]
	I/O ports at 3000 [disabled] [size=256]
	Memory at e4400000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Expansion ROM at e4420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon
```


Someone please suggest me whether my ATI chipset is off or not. If it is on, how can I turn it off and stop making it consume power and stop letting my system heat up.

---

### Post by kurt18947 on 2011-10-04
You could open "additional drivers". Where that's found depends on Ubuntu version.  If ATI drivers show up as activated, you could uninstall them. That should deactivate the ATI chipset.

---

