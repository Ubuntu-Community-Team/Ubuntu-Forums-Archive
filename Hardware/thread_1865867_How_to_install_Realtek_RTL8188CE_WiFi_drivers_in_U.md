---
title: "How to install Realtek RTL8188CE WiFi drivers in Ubuntu 11.10"
date: 2011-10-20
forum: Hardware
---

### Post by DiegoTc on 2011-10-20
Hi
I have a toshiba laptop and I am getting problems with the wifi card Realtek RTL8188CE WiFi drivers.

At the beginning the network manager told me that the driver was of, but it was on, it appear the option of wifi, but could never enable it.

I follow this guide [http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)

And anything :( Now it doesn't appears graphically.

I did a lspci -v  and have this as result

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
	Flags: bus master, fast devsel, latency 0, IRQ 10
	I/O ports at 3000 [size=256]
	Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: rtl8192ce
Any help

---

