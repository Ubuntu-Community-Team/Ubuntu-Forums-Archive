---
title: "Kubuntu 14.04 Hp 6200C flatbed scanner USB connection issue"
date: 2014-08-06
forum: Hardware
---

### Post by bweinel on 2014-08-06
Greetings all,

I'm having an issue when trying to connect my HP 6200C flatbed scanner to Kubuntu 14.04 via USB. 

When the scanner is connected, lsusb shows the scanner is there:

```

bill@speedy:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 03f0:0201 Hewlett-Packard ScanJet 6200c
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 004 Device 003: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and a look at /var/log/syslog also shows that the scanner hardware is being recognized, but says that its not a valid device:

```

Aug  6 08:38:17 speedy kernel: [ 1217.579496] usb 5-4: new full-speed USB device number 3 using ohci-pci
Aug  6 08:38:23 speedy kernel: [ 1222.760594] usb 5-4: New USB device found, idVendor=03f0, idProduct=0201
Aug  6 08:38:23 speedy kernel: [ 1222.760601] usb 5-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  6 08:38:23 speedy kernel: [ 1222.760608] usb 5-4: Product: HP ScanJet 6200C
Aug  6 08:38:23 speedy kernel: [ 1222.760611] usb 5-4: Manufacturer: Hewlett-Packard
Aug  6 08:38:23 speedy kernel: [ 1222.760613] usb 5-4: SerialNumber: SG95N11037HL
Aug  6 08:38:23 speedy logger: loading HP Device 005 003
Aug  6 08:38:23 speedy colord: Device added: sysfs-Hewlett-Packard-HP_ScanJet_6200C
Aug  6 08:38:23 speedy hp-config_usb_printer: hp-config_usb_printer[4557]: error: This is not a valid device

```
 
I checked to see that the current versions of both libsane-hpaio and hplip were loaded. I also noticed when looking at the /dev directory that there was no scanner device showing up there.

Any ideas as to where to go next?

cheers,
bill

---

### Post by bweinel on 2014-08-07
Well after some additional research I may at least have a partial answer.... I ran across this on the HP site at [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) when searching for a single function HP Scanjet 6200C:

"Sorry, HP Scanjet single function scanners are not supported by HPLIP. For possible Linux support, please visit: http://www.sane-project.org/"

Also confirmed on sourceforge at [http://sourceforge.net/projects/hplip](http://sourceforge.net/projects/hplip) .

So apparently hplip does not support flatbed scanners (...even HP flatbed scanners!) :( So its back to looking for sane backends that will support it. I do know that one existed back in v10.10.

cheers,
bill

---

