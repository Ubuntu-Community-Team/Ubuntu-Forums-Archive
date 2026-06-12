---
title: "NVIDIA Tesla s1070 with Ubuntu 8.04, any success"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by ranwei on 2009-06-18
Hi all,

I am trying to install a Nvidia Tesla s1070 unit to a Dell PowerEdge 2950 server. But the driver could not locate the hardware after installation. I have the following message using lspci -v 

0a:00.0 PCI bridge: nVidia Corporation Unknown device 05be (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=0a, secondary=0b, subordinate=0f, sec-latency=0
	Memory behind bridge: fc600000-fc6fffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Upstream Port IRQ 0
	Capabilities: [a0] Subsystem: Mediamatics Unknown device de11

(other similar devices are omitted)

Anyone has an idea?

Thank you.

---

### Post by Aetherius on 2009-08-12
Hi Ranwei,

Don't know if you ever got this working, I'm quite curious about this myself.

Have you tried the CUDA driver and softare, they have .deb's i believe.

[http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html)

Aetherius

---

### Post by Aetherius on 2009-08-12
Sorry, my mistake, its just a ".run" install binary, Still worth a shot.

---

