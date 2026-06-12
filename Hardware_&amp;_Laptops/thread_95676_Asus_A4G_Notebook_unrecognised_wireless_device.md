---
title: "Asus A4G Notebook unrecognised wireless device"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by senso on 2005-11-27
Hello,
****
I ve recently installed Ubuntu on my Asus A4G notebook and Im TOTALY excited with the o/s except (!!!) my wireless ethernet...
I have doubts about the compatibility of my hardware...?!

I tried to make the configuration with ndiswrapper executing the commands :

[B]$ndiswrapper -i sis160u.inf
$ndiswrapper -l
$modeprobe ndiswrapper
$ndiswrapper -m[/B]


I found that the "proper" driver was from SiS and got the *.INF and *.SYS from my asus drivers cd BUT in ndiswrapper documentation says that XP drivers may not work from installation cd.

My $lspci says:

[B]0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 51)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:00:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:00:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
[/B]
And my $lsusb says:

[B]Bus 003 Device 002: ID 0b05:170c ASUSTek Computer, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[/B]

My folder on /etc/ndiswrapper exists and has inside the sis160u folder with :

[B]0457:0162.0.conf 08DD:0113.0.conf 0D8E:1621.0.conf 1371:001A.0.conf sis162u.inf
08DD:0112.0.conf 0B3B:1613.0.conf 1371:0019.0.conf 1432:7119.0.conf sis162u.sys[/B]

Unfortunately $iwconfig says :

[B]lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.
[/B]

And $ifconfig -a says:

[B]eth0 Link encap:Ethernet HWaddr 00:134:33:28:B7
inet addr:192.168.2.2 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::213:d4ff:fe33:28b7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:13571 errors:0 dropped:0 overruns:0 frame:0
TX packets:11045 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13652506 (13.0 MiB) TX bytes:1552869 (1.4 MiB)
Interrupt:19 Base address:0xd800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:52310 errors:0 dropped:0 overruns:0 frame:0
TX packets:52310 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4779114 (4.5 MiB) TX bytes:4779114 (4.5 MiB)

sit0 Link encap:IPv6-in-IPv4
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)[/B]

I ve jumped to the conclusion so far that the device cannot be activated but only from the asus utility (?!) on the installation cd for XP.

My device manager though has a USB Interfeace under Silicon Intrgrated Systems [SiS] USB 2.0 Controller, called USB2.0 WLAN (although my wireless is onboard). In the device menu says :

[B]Vendor: AsusTek Computer, Inc
Device: USB Vendor Specific Interface

Status: Status
Bus Type: USB Interface
Device Type: Unknown
Capabilities: Unknown[/B]

And in the USB menu says :

[B]USB Version: 2.0
Bandwidth: 480.0 Mbits/s
Power Usage: 500mA

Vendor: AsusTek Computer, Inc
Product: USB Vendor Specific Interface
Revision: 48.2[/B]

And finally some fields from the advanced tab are :
[B]__________________________________________________ __________
(key)info.parent (type)string (value)/org/freedesktop/Hal/devices/usb_device_b05_170c_noserial
__________________________________________________ __________
(key)info.udi (type)string (value)/org/freedesktop/Hal/devices/usb_device_b05_170c_noserial_if0
__________________________________________________ __________
(key)linux.hotplug_type (type)int (value) 1 (0x1)
__________________________________________________ __________
(key)linux.sysfs_path (type)string (value)/sys/devices/pci0000:00/0000:00:03.3/usb3/3-6/3-6:1.0
__________________________________________________ __________
(key)usb.linux.sysfs_path (type)string (value)/sys/devices/pci0000:00/0000:00:03.3/usb3/3-6/3-6:1.0
__________________________________________________ __________
(key)usb.linux.device_number (type)string (value) 2(0x2)
__________________________________________________ __________
(key)usb.vendor (type)string (value) ASUSTek Computer, Inc.
__________________________________________________ __________
(key)usb.vendor_id (type)string (value) 2821 (0xb05)
__________________________________________________ __________
(key)usb.vendor_bcd (type)string (value) 512 (0x200)
__________________________________________________ __________
[/B]
I ve made quite a lot of research because Ubuntu is the most stable o/s ive ever used, and I made quite a preparation for its installation.....NO I dont want to try another lin distro...

Please I would be grateful for ANY kind of help on resolving this major issue.

Thakn u all for your time reading this.
Senso

---

### Post by brallan on 2006-03-11
My laptop is an [ASUS z9200u]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U"), with builtin ASUS 802.11g wireless card which when i look in XP says the driver is BCMWL5.sys (Broadcom corp) version 3.100.64.0 has anyone had any luck getting this wireless card to work?

EDIT: I was able to get it to work by following the instructions on:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless+card](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless+card)

works like a charm!

brian (barcelona)

---

