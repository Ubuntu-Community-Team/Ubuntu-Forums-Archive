---
title: "Installing new firewire card."
date: 2009-02-25
forum: Hardware
---

### Post by wurdien on 2009-02-25
Hi,

I need some help installing my new firewire card. I already have integrated firewire port in my computer which works, but I want to install another host card (because my old card doesn't work very well with ffado).

lspci is able to see new card, but gscanbus doesn't see it.

Card works perfectly on windows.

lspci -v
```

#Old card
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. MS-6701
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at e6426000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 60000000 [disabled] [size=128K]
	Capabilities: [64] Power Management version 2

#New card
00:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04) (prog-if 10 [OHCI])
	Subsystem: Pinnacle Systems Inc. Unknown device 000e
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at e6425000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

```

---

### Post by wurdien on 2009-02-27
I can't use card on gentoo either, so I think that I have missed some essential point installing the card. I have tried reinstalling all 1394 related drivers and kernel.

---

