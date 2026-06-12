---
title: "Avertv CaptureHD 727 PCI-E Under ubuntu 10.10 32bit?"
date: 2011-02-13
forum: Hardware
---

### Post by viktormadarasz on 2011-02-13
Hi,

Is there any workaround under ubuntu 10.10 to make my Avertv Capture HD 727 PCI-E Card work in any of the TV Watching applications, or even in XBMC?Its remote is the RM-KV which as far as i saw noone had a luck to make it work under Lirc, I hope it doesnt mean I will not be able to watch tv channels neither....

The 10 in 1 HDMI input doesnt really matter anyway just the TV Tuner part.

On Avertv website of course there is no support neither drivers for Linux ;(

lspci gives me this output:

[I]lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
**03:00.0 Multimedia video controller: Device 1a0a:6200 (rev 01)**[/I] (I guess this one should be the PCI-E TV Card,,,,)

Thanks,

Viktor

---

### Post by EggoubHTPC on 2011-02-20
Victor,

Were you able to find a solution? I'm in the same boat (but with the AVerTV HD DVR).

Phillip

---

