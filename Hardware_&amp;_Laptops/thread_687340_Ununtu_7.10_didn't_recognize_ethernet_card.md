---
title: "Ununtu 7.10 didn't recognize ethernet card"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by Malfet on 2008-02-04
I've installed Ubuntu 7.10 as a second operating system in parallel to WinXP and meet a problem: the system didn't recognize on-board ethernet card. In "Network settings" I got only Modem connection, but not Wired connection. I had no experience with Ubuntu or Linix before.
I've found several Linux drivers on the CD came with motherboard (for Mandrila2007, for RedHat and something else) and install them as described but it didn't help.
lspci command line gave follows:

```

malfet@DualCore-Ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

```

Looks like Gigabit Ethernet Adapter is there, but pppoeconf tells "There is no Ethernet interface available"

ifconfig shows

```

malfet@DualCore-Ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10352 (10.1 KB)  TX bytes:10352 (10.1 KB)

```

File /etc/network/interfaces doesn't even mention ebout eth0 interface

```

auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0






auto ppp0
``` 

Please, help. How to solve the problem?

---

### Post by jan quark on 2008-02-04
I googled and checked the hardware support for wireless cards ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported))

a bit and it looks like it isn't supported as of right now in Ubuntu which would explain why it won' work

sry

---

### Post by Yellow Pasque on 2008-02-04
Do you have a driver loaded for the NIC?
```
sudo lshw -C network
```

If not, I'm not sure what driver you need, maybe this one?:
[http://www.driverstock.com/SiS-SiS966-driver-download/28-9-5679-58855/index.html](http://www.driverstock.com/SiS-SiS966-driver-download/28-9-5679-58855/index.html)

---

### Post by Malfet on 2008-02-04
> **jan quark said:**
> I googled and checked the hardware support for wireless cards ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported))
a bit and it looks like it isn't supported as of right now in Ubuntu which would explain why it won' work
sry

That's just ordinary **ethernet** card - it has no relation to wireless.  Most common, nothing advanced, nothing complicated - just an ordinary ethernet on-board card.

---

### Post by Malfet on 2008-02-04
> **Temüjin said:**
> Do you have a driver loaded for the NIC?
```
sudo lshw -C network
```

Thanks for the answer. I got this

```

malfet@DualCore-Ubuntu:~$ sudo lshw -C network
[sudo] password for malfet:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
malfet@DualCore-Ubuntu:~$  

```

> 
If not, I'm not sure what driver you need, maybe this one?:
[http://www.driverstock.com/SiS-SiS966-driver-download/28-9-5679-58855/index.html](http://www.driverstock.com/SiS-SiS966-driver-download/28-9-5679-58855/index.html)

Perhaps, I've already found the same driver in a different place but I don't understand this. It says Install Fedora Core 3, then download Linux kernel 2.6.9... I don't understand all this. I've used two drivers for different linux-systems, which came with my motherboard. They just say copy it to a specific location and replace other sis190.ko file, but it didn't help.

PS I tried to install these driver just like it is without Fedora Core 3 ets. I edited files file "/usr/src/linux-2.6.9/drivers/net/Kconfig" and "/usr/src/linux-2.6.9/drivers/net/Makefile". But after command 'make menuconfig' no Linux Kernel configuration menu was popped. I just got long list with many errors and that's all!

---

### Post by Yellow Pasque on 2008-02-04
The instructions that talk about FC3 are out of date. Try this: [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

---

### Post by Malfet on 2008-02-04
> **Temüjin said:**
> The instructions that talk about FC3 are out of date. Try this: [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

Thanks. I'll try.

---

### Post by Malfet on 2008-02-04
> **Temüjin said:**
> The instructions that talk about FC3 are out of date. Try this: [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6)

No, it didn't work out. When I typed "make oldconfig" I got many 'warning' and 'error' messages, so I was not capable to complete it. May be, I'll try to install Ubuntu 6.06 - otherwise I'll leave it and go back to WinXP. A can apply some efforts, but not too much.

Best,
M.

---

