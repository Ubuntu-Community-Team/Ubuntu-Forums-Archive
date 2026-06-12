---
title: "impossible to activate bluetooth after wifi STA wireless driver installation"
date: 2009-12-09
forum: Hardware
---

### Post by helena_one on 2009-12-09
Hello,

I have a HP-DM1.
When I install ubuntu, the wifi doesnt work (on fresh install), but bluetooth works (I can connect with my phone a browse the files on my phone micro-SD card).

My wifi chip is a broadcom bc4312, so, as explained in many post, I have to use the Broadcom STA wireless driver (proprietary) and then the wifi works perfectly.

unfortunatly, after STA drivers install, bluetooth doesnt work anymore.

either it is deactivated, but it is not possible to activate it. or it is activated but no way to detect any bluetooth devices.

when it seems to work (but no way to connect to any device):
```
helena@prout:~$ hciconfig hci0
hci0:    Type: USB
    BD Address: 00:26:5E:C1:39:8D ACL MTU: 1021:8 SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN
    RX bytes:715 acl:0 sco:0 events:26 errors:0
    TX bytes:356 acl:0 sco:0 commands:32 errors:6
```my lsusb (the usb device is the HP one:
```
helena@prout:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:2a1d Hewlett-Packard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 5986:0182 Acer, Inc
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
my lspci, in case it could help
```
helena@prout:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```
and a part of my dmesg:
```
helena@prout:~$ dmesg |grep tooth
[    0.268012] Bluetooth: Core ver 2.15
[    0.268035] Bluetooth: HCI device and connection manager initialized
[    0.268035] Bluetooth: HCI socket layer initialized
[    1.150545] Bluetooth: L2CAP ver 2.13
[    1.150548] Bluetooth: L2CAP socket layer initialized
[    1.150553] Bluetooth: SCO (Voice Link) ver 0.6
[    1.150555] Bluetooth: SCO socket layer initialized
[    1.150610] Bluetooth: RFCOMM TTY layer initialized
[    1.150615] Bluetooth: RFCOMM socket layer initialized
[    1.150618] Bluetooth: RFCOMM ver 1.11
[    4.459654] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    8.119777] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.119781] Bluetooth: BNEP filters: protocol multicast
```
here are a few tests with hciconfig:
```
helena@prout:~$ sudo hciconfig hci0 reset
[sudo] password for helena:
Can't init device hci0: Connection timed out (110)
helena@prout:~$ sudo hciconfig hci0 down
helena@prout:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
helena@prout:~$ sudo hciconfig

hci0:    Type: USB
    BD Address: 00:26:5E:C1:39:8D ACL MTU: 1021:8 SCO MTU: 64:1
    DOWN
    RX bytes:715 acl:0 sco:0 events:26 errors:0
    TX bytes:356 acl:0 sco:0 commands:36 errors:10

helena@prout:~$
```then if I use hciconfig hci0 down: no way to activate again the bluetooth interface.
even if I use "restart computer", I have to shut it down and switch it on again.

my computer use a combo mini pci-express card for both wifi and bluetooth.

if anyone has a clue?

---

### Post by helena_one on 2009-12-13
no idea?

no body as same issue with this card? I'm pretty sure it is the same on the 311c

---

### Post by primes2h on 2009-12-23
I have openend a bug about this issue.
Please change status to "Confirmed" and then click on "I'm also affected by this bug".
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/499445](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/499445)

Thank you.

---

### Post by milan.skocic on 2010-01-09
I have the same problem with my HP mini 110.

---

### Post by marty pain on 2010-01-19
I have the same problem, but looks like we will have to lump it. 

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293)

Basically it says that the wireless drivers conflict with the bluetooth drivers and there isn't anything they can do as the wireless drivers are propriety

---

### Post by primes2h on 2010-01-26
> **marty pain said:**
> I have the same problem, but looks like we will have to lump it. 

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/385293)

Basically it says that the wireless drivers conflict with the bluetooth drivers and there isn't anything they can do as the wireless drivers are propriety

You linked the wrong bug.
This is the right one:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/499445](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/499445)

Bye.

---

### Post by jsampaio57 on 2010-03-21
I have something similar in my Toshiba Satellite Pro T110. Under Ubuntu 9.10, the BT works from scratch. To have WL, I had to install new drive (RLT8192SE). WL starts and connects. However BT can view BT devices but fails connecting. I must turn off WL, connect BT device and then turn on WL again. I must repeat this whenever I reboot the OS.

I tried 10.04 beta-1. It works great in my desktop. IN the Notebook, however it is the WL that never connects (BT ok). WL starts but does not see the wireless network. If I force the connection (providing name, password, infrastructure... etc) the WL connects but never gets a working IP addrs.

Cheers...

---

### Post by buchta on 2011-02-13
have anyone sort this out please? I think I have the same issue  on asus 1215n...

---

