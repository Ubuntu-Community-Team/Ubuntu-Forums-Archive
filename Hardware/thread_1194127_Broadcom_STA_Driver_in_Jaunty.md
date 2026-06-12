---
title: "Broadcom STA Driver in Jaunty"
date: 2009-06-22
forum: Hardware
---

### Post by sconnelly on 2009-06-22
I recently installed Ubuntu 9.04 on a Dell Inspiron with a Broadcom 4311 wireless card.  After launching Firefox, I see no internet connectivity.  I collected the following information and would appreciate any advice on the solution to my problem.

-----------------------------------------------------------------
System -> Administration -> Hardware Drivers shows:
Broadcom STA wireless driver
with a green button for the STA driver which
 "is activated and currently in use"
It says the STA driver is tested by Ubuntu developers and the license is
 proprietary.

-----------------------------------------------------------------
> lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:95:3c:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list 
       ethernet
          physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=
       5.10.79.10
          latency=0 module=wl multicast=yes wireless=IEEE 802.11
       bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:82:e3:62
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt
          10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44
          driverversion=2.0 duplex=half latency=64 link=no module=ssb
          multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:fb:8a:5f:82:ac
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3
          firmware=N/A link=yes multicast=yes

-----------------------------------------------------------------
> lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML
   and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML
   and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High
   Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express
   Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express
   Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI
   Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI
   Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI
   Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI
   Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI
   Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface
   Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family)
   SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller
   (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility
   X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX
   (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro
   Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host
   Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller
   (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g
   WLAN (rev 01)

-------------------------------------------------------------------------
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:82:e3:62  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:7e:95:3c:8a  
          inet6 addr: fe80::219:7eff:fe95:3c8a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

-----------------------------------------------------------------
> iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by stim on 2009-06-22
Well based on what you posted, the driver is in use and ready to go.  When you click on networkmanager (the two small computers in the system tray), do you get a list of wireless networks to connect to?

---

### Post by sconnelly on 2009-06-24
> **stim said:**
> Well based on what you posted, the driver is in use and ready to go.  When you click on networkmanager (the two small computers in the system tray), do you get a list of wireless networks to connect to?

I don't understand what the "system tray" is.  Is this the drop down menu that I get when i select "System" in the menu bar?  Choices are "Preferences" and "Administration".  There is one network option under each of these choices.  I searched the Ubuntu documentation for "NetworkManager" and found information on it, but I don't know how to launch this application.  I tried the command line, but with no success.  It seems to be in /usr/sbin/.  Thanks for your response.

---

### Post by sconnelly on 2009-06-24
I don't understand what the "system tray" is. Is this the drop down menu that I get when i select "System" in the menu bar? Choices are "Preferences" and "Administration". There is one network option under each of these choices. I searched the Ubuntu documentation for "NetworkManager" and found information on it, but I don't know how to launch this application. I tried the command line, but with no success. It seems to be in /usr/sbin/. Thanks for your response.

---

### Post by e-square12 on 2009-08-10
I have a similar issue. But my "Wireless Networks" is empty.

coco@coco:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
_______________________________________________
coco@coco:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:d6:29:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:11:b2:3e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.15.100 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:46:ea:ab:92:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
______________________________________________________________________________
Everytime I turn on my computer, I have to deactivate and activate again the driver just to get the "in use" part in Hardware Drivers. Any suggestions? Thanks.

---

