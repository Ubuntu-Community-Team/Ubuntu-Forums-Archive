---
title: "Unable to open USB device &quot;usb://Lexmark/E210&quot;"
date: 2005-01-12
forum: Hardware &amp; Laptops
---

### Post by Jan-42 on 2005-01-12
Hi,

I have installt my Lexmark E210 Laserprinter with the gnome-cups-manager, the program shows me the printer. But he did not print the Testpage, the gnome-cups-manager error is:
```

Unterbrochen: Unable to open USB device "usb://Lexmark/E210": No such device
```
dmesg says:
```
usb 1-1: new full speed USB device using address 4
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x0059
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

```

When i boot Gentoo everything works fine, this is not a Hardware problem. 

Why did cups first see usb://Lexmark/E210 and then tell me "No such device"? In /dev/usb and /.dev/usb is no Lexmark Folder.

Next Problem: [http://marvin:631](http://marvin:631) (and localhost, 127.0.0.1) give me an 404 "Site not found" Error. Why?

Thanks and sorry for my bad english

---

### Post by tiiim on 2005-01-12
[QUOTE=Jan-42]Hi,

I have installt my Lexmark E210 Laserprinter with the gnome-cups-manager, the program shows me the printer. But he did not print the Testpage, the gnome-cups-manager error is:
```

Unterbrochen: Unable to open USB device "usb://Lexmark/E210": No such device
```
dmesg says:
```
usb 1-1: new full speed USB device using address 4
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x0059
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

```

When i boot Gentoo everything works fine, this is not a Hardware problem. 

Why did cups first see usb://Lexmark/E210 and then tell me "No such device"? In /dev/usb and /.dev/usb is no Lexmark Folder.

Next Problem: [http://marvin:631](http://marvin:631) (and localhost, 127.0.0.1) give me an 404 "Site not found" Error. Why?

Thanks and sorry for my bad english[/QUOTE]
 try localhost:631

---

### Post by Jan-42 on 2005-01-12
[QUOTE=tiiim]try localhost:631[/QUOTE]

I have Cups reinstalled and it is running:
```
root@marvin:~ # /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System...                             [ ok ]
```

but [http://localhost:631](http://localhost:631) and [http://127.0.0.1:631](http://127.0.0.1:631) brings the "404  Not Found
The requested resource was not found on this server." Error Message

---

### Post by Jan-42 on 2005-01-12
Well my printers are now working, but only with this ugly workaround:
```
/etc/cups/printers.conf

<Printer E210>
Info E210
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<DefaultPrinter tp0>
Info Canon_PIXMA_iP5000
Location 
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
``` 
I am using [http://www.turboprint.de](http://www.turboprint.de) for the Canon.

---

