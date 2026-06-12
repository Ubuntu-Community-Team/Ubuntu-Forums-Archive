---
title: "Huawei E5372 mobile wifi not being recognised"
date: 2023-05-03
forum: Hardware
---

### Post by mangocrazy2 on 2023-05-03
I've been an Ubuntu user for many years, but still class myself as a  Linux noob. I'm trying to get my Huawei E5372 mobile wifi device  (branded Kanguru externally) to work on 22.04 but with no success. It  works well on my Windows partition (I'm dual-booting) but is not  recognised in Kubuntu. Every time I boot up it is recognised as a  Kanguru optical device and not a networking device. So my first question  is, is there any way I can stop the system mounting my device as  storage?

After skimming some other forums I issued the following commands. Note  that this is not a direct screen shot as I have to save the output on my  Windows partition in order to be able to upload to the Internet.

g@g-zen:~$ip link

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
link/ether f4:b5:20:2d:d3:8c brd ff:ff:ff:ff:ff:ff

3: wwx0c5b8f279a64: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
link/ether 0c:5b:8f:27:9a:64 brd ff:ff:ff:ff:ff:ff

g@g-zen:~$ lsusb

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 003 Device 002: ID 12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

Bus 001 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse

Bus 001 Device 003: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard

Bus 001 Device 002: ID 04f9:0027 Brother Industries, Ltd HL-2030 Laser Printer

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

g@g-zen:~$ ls /dev/ttyUSB*

/dev/ttyUSB0

g@g-zen:~$

Any help would be very gratefully received.

Graham

---

### Post by mangocrazy2 on 2023-05-04
I checked a few more things and usb-modeswitch is installed but  does not appear to be initiating the switch. ifconfig is not installed  on my system and when I tried to install net-tools, the package could  not be found. So I'm in a bit of a catch-22 ; I need the Internet to  download packages to make my Internet work... More in hope than  expectation I tried to activate wwan0 but the device does not exist  (unsurprisingly). Here is a print of my shell session:

g@g-zen:~$ sudo apt info usb-modeswitch
[sudo] password for g:
Package: usb-modeswitch
Version: 2.6.1-3ubuntu2
Status: install ok installed
Priority: optional
Section: comm
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Thorsten Alteholz <debian@alteholz.de>
Installed-Size: 142 kB
Depends: tcl, usb-modeswitch-data, libc6 (>= 2.34), libusb-1.0-0 (>= 2:1.0.9)
Suggests: comgt, wvdial
Homepage: [https://www.draisberghof.de/usb_modeswitch/](https://www.draisberghof.de/usb_modeswitch/)
Download-Size: unknown
APT-Manual-Installed: no
APT-Sources: /var/lib/dpkg/status
Description: mode switching tool for controlling "flip flop" USB devices
Several new USB devices have their proprietary Windows drivers onboard,
especially WAN dongles. When plugged in for the first time, they act
like a flash storage and start installing the driver from there. If
the driver is already installed, the storage device vanishes and
a new device, such as an USB modem, shows up. This is called the
"ZeroCD" feature.
.
On Debian, this is not needed, since the driver is included as a
Linux kernel module, such as "usbserial". However, the device still
shows up as "usb-storage" by default. usb-modeswitch solves that
issue by sending the command which actually performs the switching
of the device from "usb-storage" to "usbserial".
.
This package contains the binaries and the brother scripts.
g@g-zen:~$ ifconfig
Command 'ifconfig' not found, but can be installed with:
sudo apt install net-tools
g@g-zen:~$ sudo apt install net-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package net-tools
g@g-zen:~$ sudo ip link set wwan0 up
Cannot find device "wwan0"&#8203;

Is there any way to stop the Huawei being mounted as an optical device/storage? And is 'net-tools' available for download as a standalone .deb file?

---

### Post by mangocrazy2 on 2023-05-12
Bit of an update. The Huawei mobile wifi is in use as my internet access when at our home in France. We are only there 2-3 months of the year maximum, so it makes no sense to me to sign up for a full-time contract when it will be unused for 9 months of the year. Earlier this week I drove back to the UK and brought the desktop PC and the Huawei device I use there back to the UK, so I can continue my troubleshooting. At least in the UK if I need to download any packages I can just plug the PC into my router and use 'normal' broadband. 

But I really do need to get the Huawei figured out and working for when I next go back to France.

---

### Post by mangocrazy2 on 2023-06-05
I've been trying to get to the bottom of this and I think the root problem is that the Huawei device is initially recognised  by Linux as being a flash storage device, and not a mobile wifi device.  Every time I login the device is present as flash storage. I can eject  it, but of course the next time I boot into Ubuntu it pops back as  flash storage. This is the output I see from 'usb-devices'...

T: Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#= 2 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1506 Rev=01.02
S: Manufacturer=HUAWEI Technology
S: Product=HUAWEI Mobile
C: #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=12 Driver=option
E: Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
E: Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I: If#= 1 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=16 Driver=huawei_cdc_ncm
E: Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=4ms
E: Ad=82(I) Atr=03(Int.) MxPS= 64 Ivl=2ms
E: Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E: Ad=03(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E: Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E: Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E: Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms&#8203;

So I really need to find a way to permanently disable/detach/remove  interfaces 2 and 3.  I think that once they are unable to be recognised  at boot time, then I stand a chance of Linux recognising the network  device and installing it.

So - how do I go about disabling the usb-storage interfaces permanently?

---

### Post by mangocrazy2 on 2023-09-10
I'm back in France and I'm still unable to get my Huawei/Kanguru mobile wifi to work with Ubuntu/Kubuntu.

Does anyone have any tips on how to permanently disable the usb-storage interfaces on this device? These are interfaces #2 and #3 in the above display. With them disabled I might at least have a fighting chance of the system recognising it as a comms device.

---

### Post by jeremy31 on 2023-09-10
Check the file manager for USB removable storage and click the eject option

---

### Post by mangocrazy2 on 2023-09-12
Hi Jeremy,

Thanks for your update, much appreciated. In the past when I've ejected the USB removable storage it simply returns the next time I boot. 
I'll try via file manager - is there a way to make the 'eject' permanent and carry over after reboot?
Is the 'wireless script' applicable to my issue and should I follow the intructions and post the generated output?

Thanks,

Graham

---

### Post by jeremy31 on 2023-09-12
Does ejecting the USB removable storage allow your cellular device to work?

---

### Post by mangocrazy2 on 2023-09-13
Unfortunately not. I have installed usb-modeswitch which is supposed to switch the device from usb-storage to usbserial but that has made no difference. I was hoping I could permanently disable the usb-storage interfaces so that on boot the device would be recognised as a comms device, but can find no way to do this.

---

