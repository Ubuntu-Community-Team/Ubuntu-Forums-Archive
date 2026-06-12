---
title: "[SOLVED] A couple problems"
date: 2008-06-17
forum: Hardware
---

### Post by Lilszamora on 2008-06-17
I tried installing ubuntu on my labtop, but when I got there, the Wifi didn't work and the display would only go up to 800X600 when my labtop does 1200X800.

Heres the labtop
#
Product Height
1.5"
#
Product Width
13.2"
#
Product Weight
5.25 lbs.
#
Product Depth
9.3"
#
Processor Brand
AMD
#
Processor
AMD Turion(TM) 64 X2
#
Processor Speed
2.1GHz
#
Display Type
WXGA high-definition widescreen with BrightView technology (1280 x 800)
#
Screen Size
14.1"
#
System Bus
1600MHz
#
Cache Memory
512KB + 512KB at die Level 2
#
System Memory (RAM)
4GB
#
Type of Memory (RAM)
DDR2
#
Hard Drive Type
SATA (5400 rpm)
#
Hard Drive Size
250GB
#
Optical Drive
Double-layer DVD±RW/CD-RW
#
Optical Drive Speeds
Drive speeds not specified
#
Direct-Disc Labeling
Yes
#
Digital Media Reader or Slots
Yes, digital media card reader
#
Graphics
NVIDIA GeForce Go 7150M (UMA)
#
Video Memory
Up to 1071MB
#
Personal Video Recorder (PVR)
No
#
TV Tuner
No
#
MPEG
Yes
#
Built-in Webcam
Yes
#
Modem
56 Kbps*
*Capable of receiving 56 Kbps downloads. However, current regulations limit download speed to 53 Kbps.
#
Networking
Built-in high-speed 10/100Base-T Ethernet LAN (RJ-45 connector)
#
Wireless Networking
Built-in high-speed wireless LAN (802.11b/g)
#
S-Video Outputs
1
#
Audio
Altec Lansing
#
Speakers
Built-in stereo
#
PCMCIA Slots
1 ExpressCard/34/54
#
USB 2.0 Ports
3
#
IEEE 1394 FireWire Ports
1
#
Parallel Ports
None
#
Serial Ports
None
#
Game Ports
None
#
Laptop Weight
Ultraportable (5.5 lbs. or less)
#
Battery Type
Lithium-ion (6-cell)
#
Pointing Device
Touchpad with dedicated vertical scroll pad and on/off button
#
Operating System
Windows Vista Home Premium with SP1
#
Included Software
HP Photosmart Essentials, Quick Play; muvee autoProducer ; CyberLink DVD Suite; Microsoft Works; Adobe Acrobat Reader and more


thanks in advance, sorry for some of the Irrelevant data, but I just copied from the Best buy website...here's the actual website link
[http://www.bestbuy.com/site/olspage.jsp?skuId=8782089&productCategoryId=abcat0502003&type=product&tab=2&id=1204924952362#productdetail](http://www.bestbuy.com/site/olspage.jsp?skuId=8782089&productCategoryId=abcat0502003&type=product&tab=2&id=1204924952362#productdetail)

---

### Post by issih on 2008-06-17
For the resolution issue, you probably need to just install the latest nvidia driver. If you go to the Restricted Drivers menu item (its under System somewhere) what does it say?

If I am right, your easiest path to install a new nvidia driver is to install envyng from synaptic package manager. Running that utility will do all the work for you.

As for your wireless problem, sadly this is a common difficulty, and believe it or not we need more information :s

please open a terminal and then post the output of the following commands:

```
sudo lshw -C network
```
N.B. enter your login password when prompted.

```
ifconfig
```

[CODE]ifconfig -a[CODE]

Just say if you didn't follow anything..

Hope that helps

---

### Post by Lilszamora on 2008-06-17
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:5b:b1:dd
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```
```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:5b:b1:dd  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe5b:b1dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:990122 (966.9 KB)  TX bytes:175342 (171.2 KB)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8100 (7.9 KB)  TX bytes:8100 (7.9 KB)

```

---

### Post by issih on 2008-06-17
This thread:

[http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318)

covers how to get your wireless going, It will be much much simpler if you can use a wired connection to get internet access on the laptop in order to get the files you need.

If you have any trouble, give me a shout

Hope that helps

---

### Post by Lilszamora on 2008-06-17
yep that's the one I got ahold of from the ubuntu on hp and compaq guide thing in here...lol, but thanks for everything

---

