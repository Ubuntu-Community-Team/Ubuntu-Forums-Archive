---
title: "Intel wireless card disappeared"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by FreeFull on 2007-07-10
I was starting xUbuntu 7.04 like I usually do, and when I logged in I discovered I have no internet. I opened the terminal and typed 'ifup eth0' (yes, my wifi card is eth0). Here is the result:
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

```
Now I'm using cable (its eth1). I checked BIOS and the wireless card was enabled. I'm running IBM Thinkpad (sorry, I forgot the model). Every chipset is made by Intel and everything runs on open-source drivers. I never had problems with hardware before. I did tried using the wireless on/off shortcut but nothing in the system logs changed. I found nothing important in the syslogs. I think maybe I need a module but I don't know the name of the wireless card and I have no way to get it right now. Here is result of lspci command:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

```
It clearly doesn't show my network card. It happened after I installed AVG (I don't want to send Windows viruses to my friends) but its already uninstalled and I don't know if its related. Any help will be appreciated.

---

### Post by fredj on 2007-07-10
Open a terminal and type 'sudo lshw -class network' and post the result here.
Also check that you haven't accidentally turned off the wireless from the keyboard.
Most laptops have a key combination to switch off wireless. I know you have probably
checked this already but its worth checking again.

---

### Post by FreeFull on 2007-07-11
```
freefull@xubuntu-freefull:~$ sudo lshw -class network
Password:
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth1
       version: 81
       serial: 00:0a:e4:38:2a:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.0.2 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e0200000-e0200fff ioport:3000-303f irq:11

```

And yes, I did tried the keyboard shorcut. Nothing in the system logs changed.

---

### Post by FreeFull on 2007-07-12
Sorry to bounce this, but I really need it.

---

### Post by fredj on 2007-07-12
Well your card is there. It is eth1 and the e100 driver is being loaded for it.
Open a terminal type 'cd /etc/network' and then 'gedit interfaces' to see if your card is in the
interfaces file. Post the file here. How did you originally configure your card did you use network manager?

---

### Post by FreeFull on 2007-07-13
Ok, I already checked the interfaces file (it was one of the entries returned by 'man -k network'). Here it is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Main

iface eth1 inet dhcp



auto eth0

auto eth1

```
When I installed Ubuntu my wireless card already worked and I didn't had to configure anything (but I added the network name, just in case it connected to the other wireless network). It just suddenly disappeared. It might have been caused by the installation of AVG but it probably wasn't it (I removed AVG because I realised I don't send files to Windows users). I will check if it will work with Knoppix.

---

### Post by FreeFull on 2007-07-15
Hmm, strange. The wireless card doesn't work with Knoppix... maybe its the new kernel?

---

### Post by fredj on 2007-07-15
I suggest you edit the interfaces file and remove all the lines that refer to eth0 except for
iface eth0 inet dhcp
auto eth0

What are the wireless tools? maybe you should uninstall them as well since they don't seem to
be helping. Then click on the network manager icon in the taskbar and see if you wireless card
has become visible again.

You could also boot into the previous kernel to see if the card appears again.

---

