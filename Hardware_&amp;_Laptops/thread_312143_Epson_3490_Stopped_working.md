---
title: "Epson 3490 Stopped working"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by theboomboomcars on 2006-12-03
My Epson 3490 stopped scanning.  It used to work very well but now doesn't do anything.

When I open xsane I get: 
Failed to open device 'snapscan:libusb:002:011': Invalid argument.

When I run sane-find-scanner it finds: 
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:002:011

And the snapscan.conf has this listed for the scanner:
# Epson Perfection 3490
usb 0x04b8 0x0122

I have unplugged the scanner from the computer, unplug it from the wall, and restarted the computer and nothing has helped.

Usually when I would restart the computer the scanner would reseat the light after initial boot and while the OS is loading and it is not doing that anymore.

I am not sure if this is a hardware failure or a bad configuration.

Thanks for the help.

---

### Post by MikePiff on 2006-12-06
Epson have just released new versions of their iscan package so it might be worth trying that.Try

[URL="http://www.avasys.jp/english/linux_e/dl_scan.html"]http://www.avasys.jp/english/linux_e/dl_scan.html
[/URL]

---

### Post by theboomboomcars on 2006-12-06
Thanks, I'll try that when I get home.

---

