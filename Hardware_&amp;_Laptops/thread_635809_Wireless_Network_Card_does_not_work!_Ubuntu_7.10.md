---
title: "Wireless Network Card does not work! Ubuntu 7.10"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by muhamamd.khan7 on 2007-12-09
Dear All

I have been trying since 6 months to enable wireless network card on my Laptop **(Fujitsu-Siemens) Model: Amilo L1300**. I have installed ndiswrapper and some how my card does detect some networks but shows signal **strength 0%**.

Windows wireless card driver was installed from Fujitsu-Siemens website as per model requirement while using ndiswrapper. When i installed this driver for the first time, i noticed that card showed me some networks with their signal strength % but when i restarted the system, it only shows me the wireless networks but with 0% percentage. I have tried to put my wireless **router name = essid and network password = k** , but no gains.

Some of the related info as under.

muhammadkhan@muhammadkhan-laptop:~$ **uname -a**
Linux muhammadkhan-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

muhammadkhan@muhammadkhan-laptop:~$ **lspci**
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
**01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)**
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)

muhammadkhan@muhammadkhan-laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

**wlan0**     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

muhammadkhan@muhammadkhan-laptop:~$** lspci -v**
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at b0000000 (32-bit, prefetchable) [size=128M]
        Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: fast devsel
        Memory at 30000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at 38000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1600 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at febff000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=05, sec-latency=32
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: e0000000-efffffff
        Prefetchable memory behind bridge: a0000000-afffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1100 [size=16]
        Memory at 38080000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: medium devsel, IRQ 5
        I/O ports at 1400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at f0080400 (32-bit, non-prefetchable) [size=512]
        Memory at f0080600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

[B]01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Intersil Corporation Unknown device 0000
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e0002000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>[/B]

01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at c100 [size=256]
        Memory at e0000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1079
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: a0000000-a3fff000 (prefetchable)
        Memory window 1: e4000000-e7fff000
        I/O window 0: 0000c000-0000c0ff
        I/O window 1: 0000c400-0000c4ff
        16-bit legacy interface ports at 0001

Any ideas, where i am lacking? If anyone knows about how to solve this problem, please let me know.

---

### Post by Sjovan on 2007-12-09
maby nano /etc/network/interfaces 
and do something like this could help:

```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid the name of your network
Wireless-key alotofdigets

```

this is for a WEP cryptated network, and if you use WPA you need to isntall some stuff. should be a good tut for it here on the forum.

---

### Post by muhamamd.khan7 on 2007-12-09
I did some research on Ubuntu forum and found this forum:  **Getting wireless working in Gutsy Thinkpad T61 Intel 4965AGN** very helpful.

Following this forum, i have installed wifi-radar i.e.
**sudo apt-get install wifi-radar**

and my wireless card does detect all networks, which it was not doing before. Please find attached picture of wifi-radar in motion. At the time, i am at work and can not connect to the available networks due to unavailability of network keys, but i will definitely try it at home.

If anyone has any suggestions, that how it is working now as compare to my previous post, i would be glad to know.

---

### Post by muhamamd.khan7 on 2007-12-09
This seems that there is a bug in Network-Configuration tool of Ubuntu 7.10. As i am successfully connected wirelessly but if i see network-configuration, this shows me no network access points.:guitar:

---

### Post by theozzlives on 2008-03-03
I was wondering how well a Ubuntu Laptop that used to have Vista would work on a Lyncsys Wireless-G Network

---

