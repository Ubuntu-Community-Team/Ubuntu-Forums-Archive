---
title: "HP 8530w wireless n not working"
date: 2009-04-18
forum: Hardware
---

### Post by sirhcjw on 2009-04-18
Hi All,

I am having issues with 9.04 RC and my wireless card output of lspci bellow it works connectign to an old 802.11b AP but is very slow 80-100k/s but if i try connect to my 802.11n it just won't connect it asks for the WPA2 password but then trys to connect but never does.  The AP/router I am trying to connect to is a Linksys wag160n.

$ lspci -v

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
	Subsystem: Intel Corporation Device 1011
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	Memory at db100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 56-79-8f-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

If anyone can offer some advice I would be very greatfull.

Cheers

Chris

---

### Post by padrehomer on 2009-04-19
I am having a similar issue.

Netgear wireless card with trendnet router. Was using WPA with 9.04 beta, updated to RC and its doing the same thing, not connecting.

---

