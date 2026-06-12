---
title: "RTL8111/8168B: try for Gigabit or JUNK IT?"
date: 2011-02-21
forum: Hardware
---

### Post by leespa on 2011-02-21
Hi,

Have an **RTL8111/8168B NIC** installed in Asus P7H55-M. Running Ubuntu minimal 10.10 x86_64.

I dloaded, installed the RealTek drivers and _DO HAVE this NIC working_, however:

a) I only get it to run at 100 Mbps no matter what I try using ethtool, etc. Either 100M or its broken / NO LINK.
b) Even when I do hear people say they got Gigabit or even 100 Mbps I hear nothing but horror stories about unstable performance, etc over the long-term.

QUESTION IS: **Has anyone gotten this RTL8111/8168B NIC working well under Ubuntu 10.x AT GIGABIT SPEEDS + RELIABLY?**

If so please let me know how.

If answer is NO I am going ahead with purchase of an Intel PRO/1000 CT; why make things more difficult if this NIC is simply a POS? :p

Thanks for any feedback.

---

### Post by Stettin on 2011-03-17
Can you list the steps you did to get yours working at least at 100Mbps? I'd be happy get get at least that since my bottleneck in my office is a powerline adapter that seems to max out around 60-70Mbps

---

### Post by leespa on 2011-03-17
Sure. This forum has info too [http://ubuntuforums.org/showthread.php?t=1022411&page=8](http://ubuntuforums.org/showthread.php?t=1022411&page=8)

Basic problem is that it using the r8169 driver and should be using the r8168 driver instead. This is also only specific to specific rev's of this card. rev 6 doesnt work for me; rev 3 in a different PC works great.

a) Dload Linux drivers from the RealTek site here: http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP

b) unzip and look at the readme; basically just need to run 'sudo ./autorun.sh' to do the installation of the new driver.

c) add the following line to this file /etc/modprobe.d/blacklist
blacklist r8169

d) reboot; proper r8168 module should be loaded now

What it looked like when it worked. Can not push it to Gigabit. Replaced it with an Intel PRO/1000 CT Desktop Gigabit Ethernet Network Adapter PCI Express NIC OEM and disabled this NIC.

$sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok

$sudo ethtool -i eth0
driver: r8168
version: 8.021.00-NAPI
firmware-version: 
bus-info: 0000:02:00.0

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 8432
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at e800 [size=256]
	Memory at f4fff000 (64-bit, prefetchable) [size=4K]
	Memory at f4ff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number xxxxxxxxxxxx
	Kernel driver in use: r8168
	Kernel modules: r8168

---

