---
title: "No printer detected (hp:/no_device_found)"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by breaking on 2008-02-07
Hi, when I try to add a printer (Epson Stylus D88 ) using the KDE printer manager in Kubuntu Dapper 6.06 I find that the options 'parallel/usb' are greyed out. 

'lsusb' and 'dmesg' in the terminal show that the system can actually detect the printer in the usb port though: 

-lsusb: Bus 001 Device 008: ID 04b8:0005 Seiko Epson Corp. Stylus Printer. 

-dmesg|grep lp0: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005

When I try to install the printer using CUPS through localhost:631 in the broswer I get the message 'hpiod: invalid uri:hp:/no_device_found' in the drop down menu where I would expect to see my USB connection detected. 

I tried selecting the option 'hp:/no_device_found' and going ahead with the installation of the printer regardless, but when I try to print a document I (unsurprisingly) get an error message:

'no_device_found: INFO: open device failed; will retry in 30 seconds...'

...after which it just gives up saying:

unable to send Event hp:/no_device_found 34 5012: Broken pipe'

Typing 'ls -l /dev/lp*' in the terminal tells me that the file does not exist, but if I load the lp, ppdev, parport, and parport_pc modules and then restar cupsys it does show up, with the following permissions:

-rw-r--r-- 1 root root 6 2008-02-07 17:08 /dev/lp0

Unfortunately, it does not seem to make a difference to the original problem, though. The printer still isn't recognised when I try to install it (getting instead the 'hp:/no_device_found' both in CUPS through localhost and in the KDE printer manager).

sudo -u cupsys /usr/lib/cups/daemon/cups-deviced 1 1 `id -u cupsys` '' gives:

DEBUG: [cups-deviced] Added device "beh"...
DEBUG: [cups-deviced] Added device "bluetooth"...
unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 94
unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 720
DEBUG: [cups-deviced] Added device "hp:/no_device_found"...
DEBUG: [cups-deviced] Added device "smb"...
Content-Type: application/ipp

Gattributes-charsetutf-8Httributes-natural-languageen-USD
                                                         device-classnetworkA
                                                                             device-infoBackend Error HandlerAdevice-make-and-modelUnknownE

---

