---
title: "Second monitor not detected in 17.10"
date: 2018-03-15
forum: Hardware
---

### Post by soylentjosh on 2018-03-15
I'm running Ubuntu 17.10 on a Minix N42C-4 mini pc ([specs]("http://www.minix.us/products/N42C-4.html")) and having trouble configuring a dual monitor setup. The box has 3 video outputs; HDMI (4k@30hz), USB-C (4k@60hz), and Mini Displayport (4k@60hz). My primary display is an LG [34UM69G-B]("http://www.lg.com/us/monitors/lg-34UM69G-B-ultrawide-monitor") 34" computer monitor, and secondary display is an LG smart tv ([49UJ63]("http://www.lg.com/us/tvs/lg-43UJ6300-4k-uhd-tv"), connected through the HDMI port labeled "ARC" per recommendations from the Minix website forum). I can get either of the monitors to work individually through the computer's HDMI output, but my preferred setup would be dual monitors running through the USB-C and the Mini Displayport outputs to utilize the higher refresh rate @ 60hz. 

The computer uses an Intel HD Graphics 505 driver, which from my best understanding of my research should be recognized within Ubuntu's default driver packages. The USB-C and Mini Displayport outputs aren't recognized in System Settings>Devices>Displays, or in xrandr. The output of *xrandr --listmonitors* is:

> Monitors: 1
 0: +XWAYLAND0 2560/800x1080/340+0+0  XWAYLAND0

The output of *lspci* is:

> 00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Integrated Graphics Controller (rev 0b)
00:0e.0 Audio device: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b)
00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)
00:13.0 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #2 (rev fb)
00:13.2 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #3 (rev fb)
00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)
00:1c.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
02:00.0 Network controller: Intel Corporation Device 24fb (rev 10)

Can somebody please help me get all my video outputs working so I can use dual monitors?

Thank you,
Josh

---

