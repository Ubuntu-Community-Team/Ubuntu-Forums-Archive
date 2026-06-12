---
title: "ZOTAC ZBOX CI320 nano problem with USB after install Ubuntu 14.04"
date: 2015-01-30
forum: Hardware
---

### Post by belmontpier on 2015-01-30
I have installed the 14.04 64 bit server on the ZBOX CI320 nano and I am getting this errors at every boot


 4.055278] Switched to clocksource tsc
[    4.084832] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    4.901542] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    5.718141] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    6.534805] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    7.145136] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[    7.203360] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    8.076059] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    8.892872] ehci-pci 0000:00:1d.0: port 1 reset error -110
[    9.709428] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   10.526121] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   11.136420] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   11.194636] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   12.067246] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   12.884122] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   13.700662] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   14.517334] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   15.127669] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   15.185885] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   16.058584] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   16.875370] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   17.691910] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   18.508575] ehci-pci 0000:00:1d.0: port 1 reset error -110
[   19.118902] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   19.118931] hub 1-0:1.0: unable to enumerate USB device on port 1



user@nano:~$ lspci -nnk | grep -iA2 usb
00:14.0 USB controller [0c03]: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35] (rev 0e)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:b219]
    Kernel driver in use: xhci_hcd
--
00:1d.0 USB controller [0c03]: Intel Corporation ValleyView USB Enhanced Host Controller [8086:0f34] (rev 0e)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:b219]
    Kernel driver in use: ehci-pci
user@nano:~$ uname -a
Linux nano 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

user@nano:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
zsolt@nano:~$ cat /sys/bus/usb/devices/usb*/power/control
on
on
on
user@nano:~$ 

:mad:

by the way should I enabled or disable xHCI hand-off in BIOS setup?

[h=1][/h]

---

