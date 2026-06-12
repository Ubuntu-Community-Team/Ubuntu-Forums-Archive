---
title: "Wireless adapter for IBM a31p (edgy)"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by linlap on 2006-11-05
I just installed edgy on my IBM a31p laptop, a fresh install. When the laptop had dapper the wireless card worked, but with edgy - no dice.

I did a server install and then installed the package xubuntu-desktop.

So, any suggestions on how to get the wireless running?

Oddly enough the prism2_pci module was loaded, which wasn't needed before:

```
$ lsmod |grep -E "orinoco|pris"
orinoco_pci             7168  0
orinoco                41748  1 orinoco_pci
hermes                  8576  2 orinoco_pci,orinoco
prism2_pci             72960  0

```And I have something in the system:

```
$[FONT=Courier New] [FONT=System]ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:f0a06000-f0a07000[/FONT][/FONT]

```Also, lspci shows the card:

```
$ lspci 
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
02:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

```And /var/log/messages shows:

```
Nov  4 23:50:11 linlap kernel: [17179594.088000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
Nov  4 23:50:11 linlap kernel: [17179594.088000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Nov  4 23:50:11 linlap kernel: [17179594.088000] A Prism2.5 PCI device found, phymem:0xf8000000, irq:11, mem:0xf0a06000

```

and one last hint:

```
$ sudo iwconfig wlan0
wlan0     no wireless extensions.
```

---

### Post by linlap on 2006-11-05
Well, I just got it working...  a simple

```
sudo aptitude install linux-wlan-ng

```

and reboot did the trick.

A thanks to [http://www.astro.unibas.ch/~loeffler/thinkpad/p3-kernelconf.xhtml#wireless](http://www.astro.unibas.ch/~loeffler/thinkpad/p3-kernelconf.xhtml#wireless)

It just wasn't easy... Maybe linux-wlan-ng should be installed?

---

