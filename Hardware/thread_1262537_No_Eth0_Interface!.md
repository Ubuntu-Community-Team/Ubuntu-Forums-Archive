---
title: "No Eth0 Interface!"
date: 2009-09-10
forum: Hardware
---

### Post by tuco penguin on 2009-09-10
I've installed various versions of Ubuntu on several different desktop PCs and the NIC always seems to "just work."  But I've been happily using my new Acer notebook (5739G) for several weeks with a good wireless interface, when today I decided I wanted a wired interface.  Lo and behold, it doesn't work.  In fact, there is no Eth0 or Eth1 interface listed in the Network Connections utility at all.

I'm running Ubuntu 9.04.  I confirm that the network interface is present and working by booting up in Vista.  The Ubuntu Network Connections utility seems mostly useless.  Any help would be greatly appreciated.  Let me know where to start and if the output of any queries would be helpful.  I've searched all over the internets for similar problems and have seen some interesting output within my terminal, but right now it is late and my head is spinning, so the interesting points escape me.  I'm alive with a wireless connection, but I think I must have working wired ethernet in the long term... please help!

TIA

---

### Post by Fafler on 2009-09-10
Please post output from:
```
lspci -v
ifconfig -a
```

---

### Post by tuco penguin on 2009-09-10
:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f0404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: c0000000-c00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2299
	I/O ports at 18f0 [size=8]
	I/O ports at 18e4 [size=4]
	I/O ports at 18e8 [size=8]
	I/O ports at 18e0 [size=4]
	I/O ports at 18c0 [size=32]
	Memory at f0404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: medium devsel, IRQ 10
	Memory at c0200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0652 (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at c0000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: fast devsel, IRQ 10
	Memory at c0100000 (64-bit, non-prefetchable) [disabled] [size=256K]
	I/O ports at 3000 [disabled] [size=128]
	Capabilities: <access denied>



*  *  *  *  *  *  *  *  *  *

:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr 1e:0e:f5:ce:67:c1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:21:1f:14  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:fe21:1f14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:494588 (494.5 KB)  TX bytes:114103 (114.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FA-21-1F-14-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by tuco penguin on 2009-09-10
This part looks bad:

09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
Subsystem: Acer Incorporated [ALI] Device 021e
Flags: fast devsel, IRQ 10
Memory at c0100000 (64-bit, non-prefetchable) [disabled] [size=256K]
I/O ports at 3000 [disabled] [size=128]
**Capabilities: <access denied>**

[I]EDIT:
...never mind.  I just realized I hadn't run the command with superuser priviliges.  Ran again and got the full capabilities of the NIC also:

09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: fast devsel, IRQ 10
	Memory at c0100000 (64-bit, non-prefetchable) [disabled] [size=256K]
	I/O ports at 3000 [disabled] [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-8b-23-00-dc-b8-d1-ff

Thanks again to anyone who helps track down my problem![/I]

---

### Post by Fafler on 2009-09-10
[http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html](http://dtbaker.com.au/random-bits/ubuntu---ethernet-controller-attansic-technology-corp.-device-1063-rev-c0-.html)

... or...

[http://cgi.ebay.co.uk/10-100-USB-Ethernet-Network-LAN-Adapter-NIC-RJ45-Card_W0QQitemZ290341464859QQcmdZViewItemQQptZLH_DefaultDomain_0](http://cgi.ebay.co.uk/10-100-USB-Ethernet-Network-LAN-Adapter-NIC-RJ45-Card_W0QQitemZ290341464859QQcmdZViewItemQQptZLH_DefaultDomain_0)

---

### Post by tuco penguin on 2009-09-10
Great, thanks!  I will try building the network driver today.  Nice idea using a cheap USB adapter as a backup, too.

---

### Post by tuco penguin on 2009-09-10
Well, substituting the command "sudo modprobe atl1e" for "modprobe arl1e" SEEMED to do the trick.  I noticed the suggested download seemed to contain a file with a different name than in the instructions (thus the change to "atl1e") and I tried "sudo" when I got a permission denied error.  Now I can see an Eth0 interface with "ifconfig -a"  However, it is not active.  Not sure how to get it working.  Eth0 does not show up in the Network Configuration utility.

PS--I love that I can get help in the forums like this.  Better than any customer service I've ever experienced from ANY corporation that I'd already given money to!  Thanks Fafler!


:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:d1:b8:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  ...

---

### Post by tuco penguin on 2009-09-10
Problem Solved.

I added an Auto Eth0 wired connection in Network Configuration utility (aka Network Manager).  This did not do the trick.  I found a thread elsewhere that suggested commenting all the wired connections (eth0, eth1) out of /etc/network/interfaces in order to allow Network Manager to manage my wired network connections.  Tried it and this worked!

---

