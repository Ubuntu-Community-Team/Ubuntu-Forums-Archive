---
title: "USB Lan adapter issues"
date: 2008-11-14
forum: Hardware
---

### Post by Sarmacid on 2008-11-14
Hey guys,

I'm having some problems trying to get an usb-lan adapter to work on a pc with Ubuntu 8.04 server. I have no graphical interface so it all has to be done by the console, wich I am comfortable with.

So here's what's up, when I plug it and run dmesg, I see some lines concerning the adapter```
[   97.193642] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   97.412619] usb 5-2: configuration #1 chosen from 1 choice
[   97.502835] usb0: register 'dm9601' at usb-0000:00:1d.1-2, Davicom DM9601 USB Ethernet, ff:ff:ff:ff:ff:ff
[   97.502844] usbcore: registered new interface driver dm9601

```So far so good I guess, I run```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 21:21:5a:43:e6:4b
          inet addr:172.16.232.99  Bcast:172.16.232.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5aff:fe59:e64c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:150791 (147.2 KB)  TX bytes:64179 (62.6 KB)
          Memory:f0200000-f0220000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```But when I try to shutdown eth0 and configure usb0```
ifconfig eth0 down
ifconfig usb0 172.16.232.102 netmask 255.255.255.0
```I get(only on the second command)```
SIOCSIFFLAGS: Invalid argument
```
if I run ifconfig I can only see the loopback interface, but if I run ```
ifconfig usb0
``` I get ```
usb0      Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff
          inet addr:172.16.232.102  Bcast:172.16.232.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'm not using DHCP, setting static addresses. I got a CD with the makefile for the driver but I think that the driver is already installed. Can anyone help me with this?

---

### Post by bford16 on 2008-11-14
Research suggests an IRQ conflict.  See: <http://linuxmafia.com/faq/VALinux-kb/siocsifflags-error.html>
"Q: Ethernet networking is not working. I get the error message:

"SIOCSIFFLAGS: Try again"

from ifconfig.

A: This usually indicates a hardware conflict with your ethernet controller. Run "ifconfig -a" and check the IRQ and I/O addresses used by the controller. Also, look at the contents of the files /proc/interrupts and /proc/pci to determine what IRQ and I/O addresses are in use on your system. Many ethernet and SCSI drivers cannot share interrupts under Linux. Your system most likely has an IRQ conflict.

To fix IRQ conflicts on PCI bus systems, you can often go into the motherboard BIOS setup and mark the conflicting IRQ as "Used by an ISA Device". This will force the motherboard to reassign the IRQ, often eliminating the conflict."

---

### Post by Sarmacid on 2008-11-14
I went into the bios and changed the IRQ for the usb ports and but it still doesn't works.

---

