---
title: "Setup dual monitors for ThinkPad T400 with Intel video card"
date: 2010-01-18
forum: Hardware
---

### Post by wguocan on 2010-01-18
Hi everyone, 
I am new to Xubuntu so please be nicer to me:)
I have xubuntu 9.10 installed in my ThinkPad T400 loptop. I guess I am using Intel build-in video card based on the results of lspci.
At work I have an external monitor. I want to have my LCD and external monitor to settup. How can I setup dual monitors???

 ```
The results of lspci are:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)

lspci -v
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Lenovo Device 20e4
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


```
Any ideas are greatly appreciated!!!

Chris

---

### Post by wguocan on 2010-02-03
Hi everyone,

I need to setup dual monitors for my work. It is a big deal to me. I have been searching all kinda solutions, but nothing seems working for me. So any ideas will be appreciated!

---

### Post by wguocan on 2010-02-06
Hi everyone,

Just in case someone had the similar issue as me. Here is the solution I want to share with you:
1. Download grandr and install it using Synaptic Package Manger
2. Connect the external monitor
3. Click Applications --> System --> Multiple Screens 
4. You will see LVDS1 and VGA1 in the Outputs panel and It is easy to configure dual display.

Cheers,
Chris

---

### Post by vinpa on 2011-07-13
> **wguocan said:**
> Hi everyone,

Just in case someone had the similar issue as me. Here is the solution I want to share with you:
1. Download grandr and install it using Synaptic Package Manger
2. Connect the external monitor
3. Click Applications --> System --> Multiple Screens 
4. You will see LVDS1 and VGA1 in the Outputs panel and It is easy to configure dual display.

Cheers,
Chris


I know this is an old thread, but I wanted to say thank you for this simple solution.

---

