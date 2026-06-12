---
title: "laptop idle issues (wireless)"
date: 2009-05-07
forum: Hardware
---

### Post by Tenn lynx on 2009-05-07
Hi

the upgrade to jaunty brought with it an annoying issue; when I close the lid on my laptop or if I let it idle to the point where the screen saver turns on, my wireless connection stops functioning correctly...

It still shows the status of being connected and it still shows changes in signal strength, but any data transfer over wlan is not working...
So as far as the system is concerned, it still thinks it has a working connection, so it doesn't attempt to even reconnect...

any ideas?

HP pavilion dv7 1120em

lspci -v
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at de000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number b2-04-a5-ff-ff-5d-21-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```
some dmesg errors:
```
[79553.616691] iwlagn: Read index for DMA queue txq_id (2) index 226 is out of range [0-256] 248 230
[79556.378005] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[79556.394542] iwlagn: Can't stop Rx DMA.

```

---

### Post by Tenn lynx on 2009-05-07
ok so this seems to not be a system/driver issue. As far as I can tell right now, the only way to reproduce the bug is to have Deluge (a torrent client) running. If Deluge is not running the issue seems to be gone...

---

