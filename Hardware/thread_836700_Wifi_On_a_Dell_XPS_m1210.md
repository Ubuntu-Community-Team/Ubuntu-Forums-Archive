---
title: "Wifi On a Dell XPS m1210"
date: 2008-06-21
forum: Hardware
---

### Post by Enkaybee on 2008-06-21
I installed Gutsy back in December, and upgraded to Hardy in April.  I had never needed to use Wifi because I always had a wired connection at college.  But when I left for the summer I had to start using it.  It looks like Ubuntu is detecting my linksys router and says that it has good signal strenth, but I can't get online with it.  I tried fiddling with the IP address and other information in the wireless options menu through system > administration > networking, but still got nothing.  

Can anyone help me get online without having to use my Vista dual-boot?

---

### Post by dark_phantom on 2008-06-21
Which network card do you have?  Is the wireless router configured to use encryption?  Are you able to see a wlan0 if you do an ifconfig?  Post some more details, ie. lspci, ifconfig -a, etc.

---

### Post by Enkaybee on 2008-06-22
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01d7
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at ecbfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

The router is set up for DHCP

ifconfig returns the following:

eth0      Link encap:Ethernet  HWaddr 00:18:8b:d5:76:8f  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fed5:768f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3720624 (3.5 MB)  TX bytes:519966 (507.7 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1b:77:5f:f2:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:1b:77:5f:f2:ee  
          inet addr:169.254.10.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:972 (972.0 B)  TX bytes:972 (972.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-5F-F2-EE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci returns the following:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I'm still not too great at using Ubuntu, so thanks in advance.

---

### Post by dark_phantom on 2008-06-22
It would seem you need a wrapper for your wireless card, I'm not 100% sure.  I don't have experience with the Intel 3945ABG card.

Try doing what chili555 suggested and see if that works.  [http://ubuntuforums.org/showthread.php?t=782365](http://ubuntuforums.org/showthread.php?t=782365)

PS.  Based on this link [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi), your card should be supported with the latest (hardy) kernel.

---

### Post by Enkaybee on 2008-06-23
Thanks! It works perfectly now!

---

