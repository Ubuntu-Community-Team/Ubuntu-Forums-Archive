---
title: "DELL Inspiron 7347 bluetooth issues"
date: 2015-09-14
forum: Hardware
---

### Post by u-michele on 2015-09-14
I'm having some bluetooth issues with my DELL Inspiron 7347 on Ubuntu 14.04. This pc comes with Windows preinstalled which I replaced with Ubuntu 14.04. (more information of the system below)


The bluetooth seems to work with both basic commands and the Bluetooth Manager GUI, and the scanning, connection/pairing operations are working fine.


On my Python application I have to connect up to 5/6 devices on a single session and I use rfcomm for the connection and python-serial for the data exchange. The problem comes out sometimes when the application connects with the devices (using multiple threads). Sometimes the rfcomm connection doesn't work, sometimes the initial data exchange. It's very unpredicatable and difficult to spot the problem(s). Even the connection with one device sometimes fail, so I assume it's not a thread problem.


The problem occours on Ubuntu 15.04, 13.10 and 13.04 too.


I found this bug on lauchpad similar to my issue but the solutions posted are not working.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237296)


System Infos:


```
dmidecode | grep -A3 '^System Information'

System Information
    Manufacturer: Dell Inc.
    Product Name: Inspiron 7347


uname -a
Linux zotac-Inspiron-7347 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




dmesg | grep -i Bluetooth
[   15.544460] Bluetooth: Core ver 2.20
[   15.544486] Bluetooth: HCI device and connection manager initialized
[   15.544491] Bluetooth: HCI socket layer initialized
[   15.544494] Bluetooth: L2CAP socket layer initialized
[   15.544501] Bluetooth: SCO socket layer initialized
[   17.650311] Bluetooth: RFCOMM TTY layer initialized
[   17.650320] Bluetooth: RFCOMM socket layer initialized
[   17.650325] Bluetooth: RFCOMM ver 1.11
[   17.656045] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.656049] Bluetooth: BNEP filters: protocol multicast
[   17.656053] Bluetooth: BNEP socket layer initialized


 lspci -tv
-[0000:00]-+-00.0  Intel Corporation Haswell-ULT DRAM Controller
           +-02.0  Intel Corporation Haswell-ULT Integrated Graphics Controller
           +-03.0  Intel Corporation Haswell-ULT HD Audio Controller
           +-04.0  Intel Corporation Device 0a03
           +-14.0  Intel Corporation Lynx Point-LP USB xHCI HC
           +-16.0  Intel Corporation Lynx Point-LP HECI #0
           +-1b.0  Intel Corporation Lynx Point-LP HD Audio Controller
           +-1c.0-[01]----00.0  Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           +-1d.0  Intel Corporation Lynx Point-LP USB EHCI #1
           +-1f.0  Intel Corporation Lynx Point-LP LPC Controller
           +-1f.2  Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode]
           +-1f.3  Intel Corporation Lynx Point-LP SMBus Controller
           \-1f.6  Intel Corporation Lynx Point-LP Thermal

```

Any idea on the problem? Tell me if you need more information.

---

### Post by jeremy31 on 2015-09-14
Does it still happen with wifi off?
```
rfkill block wifi
```
And you can use rfkill unblock wifi to enable

---

### Post by u-michele on 2015-09-16
It happens even with an external bluetooth dongle.

---

