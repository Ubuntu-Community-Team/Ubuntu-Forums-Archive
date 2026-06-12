---
title: "Problems with printer/(USB?) (HP1010)"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by jacke on 2004-12-29
I have just reinstalled my computer with Ubuntu linux (had Suse 8.1 before). But I can't get my printer to work.  
I add my printer using gnome-cups-manager, using driver hpijs, but when I try to print a test page the job just gets paused and I get this error in the printer properties:
```

Paused: Unable to open USB device "usb://HP/LaserJet%201010": No such device
```

I think the problem might be related to USB, because this printer works well connected to another computer running Ubuntu. 
lsusb returns this:
```
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:0c17 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000

```
Dmesg tells me this when I plugin the printer:
```
usb 1-2: new full speed USB device using address 4
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0C17

```
The modules loaded for USB are:
usbcore, uhci_hcd, usblp

Link to cupsd error log file (loglevel set to debug):
[http://jacke.hjolug.org/cups_error_log.txt](http://jacke.hjolug.org/cups_error_log.txt)

My chipset is some "VIA Apollo PRO133x", if that's of any help...
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
```

Any ideas of what possibly could cause this problem would be really appreciated, because I'm in dire need of getting this printer to work.

---

