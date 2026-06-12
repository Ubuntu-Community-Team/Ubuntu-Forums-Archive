---
title: "Find out Driver for Network Card"
date: 2011-12-14
forum: Hardware
---

### Post by jesuisbenjamin on 2011-12-14
Hello,

I use 11.04 on a Dell Vostro 1510 and it works just fine. I've tried Fedora 15 some time ago and, unlike Ubuntu, it didn't provide me with the necessary driver for my Network Card.

How can I find out what is the required driver for my card and would that be the same driver for all distro's?

Thanks.

---

### Post by dandnsmith on 2011-12-14
I think the driver would be the same.
Use Ubuntu to get to it - in a terminal window do:
*sudo lspci -v*
and inspect the results to find the network card bits, where you will find it names the kernel driver in use.

---

### Post by jesuisbenjamin on 2011-12-14
This is what [FONT="Courier New"]lspci[/FONT] returns:

```
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 7b-b0-5f-ff-ff-18-00-22
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Dell Device 0273
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 5000 [size=256]
	Memory at f8610000 (64-bit, prefetchable) [size=4K]
	Memory at f8600000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f8620000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

I'm not sure I should look at Ethernet Controller or Network Controller (perhaps both?)
I suppose the driver is here [FONT="Courier New"]r8169[/FONT] and / or [FONT="Courier New"]wl[/FONT]. Now, can I get hold of these and save them on a USB for install or so?

---

### Post by dandnsmith on 2011-12-14
OK - so the first bit of information is that the module is r8169 - which is unfortunate because (as I, for one, can attest) the r8169 module for RTL 8111/... gives trouble (certainly with Ubuntu and Mint), and is best replaced by the r8168.

Unless someone looking on knows how to get them and transfer them to Fedora, I'll have to do a bit of digging.

You could have a look at the output of the lspci -v under Fedora, just for comparison to see if any driver has been loaded.

---

### Post by TBABill on 2011-12-14
Your wireless card is a Broadcom BCM4312, very common in a variety of brands of laptops. I exclusively use the STA driver, whose module is wl. In Ubuntu you have an automated GUI to help install the driver, or it can also be done manually via terminal. In each distro the process to activate the driver may vary, particularly in distros that do not offer the proprietary software in their repos. You are then faced with adding external sources, such as RMPForge I think for Fedora (correct me if that's wrong, please) or Debian's multimedia repo. And the steps to install and enable are different between all I have mentioned.
 
If you go to Broadcom's site and pull their driver for Linux, there's a readme file that contains the steps to install it in various distros. Keep that on a thumb drive and you can then use it from distro to distro.
 
Note that the card is also supported (some versions of the BCM4312) by the b43 driver, which is open source. However, it still needs Broadcom's firmware so you'll still have that piece to contend with. Either way, the proprietary bits come into play and those may be what causes some of the differences in availability and ease of installation between various distros. Some, like Ultimate Edition and Pinguy, include the drivers right on the disk, as does Ubuntu (but most don't realize that).

---

### Post by sebrustiina on 2012-11-01
hello! i have broblem. i have net card (WIRELESS LAN PCI CARD 54 MBPS könig)
[http://www.konigelectronic.com/en_us/computer/networking/1023728](http://www.konigelectronic.com/en_us/computer/networking/1023728)
but i didnt have driver to netcard can u help me please:)

---

