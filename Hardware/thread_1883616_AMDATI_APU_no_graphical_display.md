---
title: "AMD/ATI APU no graphical display"
date: 2011-11-19
forum: Hardware
---

### Post by Maintech on 2011-11-19
Ok. I have waited many weeks for a resolution to the issue with AMD/ATI APU graphics. I have tried 'nomodeset', 'radeon mode=0', and 'radeon mode=1' with no video after booting from live disk. I have tried vesa mode, and 'mode=771'. I have tried combinations. I am running Ubuntu 11.04 now on the computer with the AMD/ATI APU graphics and making this post with it. No issues. What has been broken in all flavors of linux to cause the graphics display to no longer work??? No version of linux (new versions) will work anymore. Not Fedora, not SuSE, not Ubuntu, NOTHING......with the new kernels. My computer is a HP Pavilion dv6z quad-core APU with the built-in APU graphics adaptor from ATI. Only the **OLD** versions of linux will work with it. Will I have to give up using linux on it or use only MS???? I have been a long time user of linux and it is my preferred OS but I like to keep it current. I can continue to use 11.04 for a time but eventually there will be no support for it. Then what? :confused:

**lspci -v from working 11.04 on HP Pavilion Laptop**

VGA compatible controller: ATI Technologies Inc Device 9641 (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 358b
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=256]
	Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

---

