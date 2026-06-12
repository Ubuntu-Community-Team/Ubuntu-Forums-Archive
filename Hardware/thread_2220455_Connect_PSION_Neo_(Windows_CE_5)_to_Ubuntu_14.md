---
title: "Connect PSION Neo (Windows CE 5) to Ubuntu 14"
date: 2014-04-28
forum: Hardware
---

### Post by Stanny_Nuytkens on 2014-04-28
Hi all,

I'm trying to get my PSION Neo device working as usb device in Ubuntu.
This device connects through a cradle to my HP Envy 17-j000eb USB 3.0 port.

_lsusb_

> stanny@ENVY:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
**Bus 003 Device 007: ID 045e:00ce Microsoft Corp. Generic PPC Flash device**
Bus 003 Device 003: ID 046a:0021 Cherry GmbH CyMotion Expert Combo
Bus 003 Device 005: ID 138a:0050 Validity Sensors, Inc. 
Bus 003 Device 002: ID 046d:c06a Logitech, Inc. USB Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


_tail -f /var/log/syslog_ when connecting the device:

> Apr 28 08:38:50 ENVY kernel: [  920.376063] usb 3-4: new full-speed USB device number 9 using xhci_hcd
Apr 28 08:38:50 ENVY kernel: [  920.393757] usb 3-4: New USB device found, idVendor=045e, idProduct=00ce
Apr 28 08:38:50 ENVY kernel: [  920.393766] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 28 08:38:50 ENVY kernel: [  920.393772] usb 3-4: Product: Psion Teklogix PX750 serial device
Apr 28 08:38:50 ENVY kernel: [  920.393776] usb 3-4: Manufacturer: Psion Teklogix
Apr 28 08:38:50 ENVY kernel: [  920.394540] ipaq 3-4:1.0: PocketPC PDA converter detected
Apr 28 08:38:50 ENVY kernel: [  920.394810] usb 3-4: PocketPC PDA converter now attached to ttyUSB0
Apr 28 08:38:50 ENVY mtp-probe: checking bus 3, device 9: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Apr 28 08:38:50 ENVY mtp-probe: bus: 3, device: 9 was not an MTP device

But I don't see anything under [U]fdisk -l

[/U]>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT


I had to remove modemmanager because I was getting these errors:

> Apr 23 14:46:02 ENVY ModemManager[863]: <warn>  (ttyUSB0): port attributes not fully set
Apr 23 14:46:20 ENVY ModemManager[863]: <info>  Creating modem with plugin 'Generic' and '1' ports
Apr 23 14:46:20 ENVY ModemManager[863]: <warn>  Could not grab port (tty/ttyUSB0): 'Cannot add port 'tty/ttyUSB0', unhandled serial type'
Apr 23 14:46:20 ENVY ModemManager[863]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4': Failed to find primary AT
port

I wish to use this device through Virtualbox to continue working on a Windows CE5.0 .Net project
but first I need to get this device recognized/working under Ubuntu before I can even try to map it through Virtualbox...

I have gone from Windows to Debian(server) & Ubuntu (desktop) since a few weeks.
I've setup a squid proxy server with squidguard and AD auth so I like to think myself a moderate noob. :D

I hope someone can help me out here...

Thanks for your time!

Stanny

---

