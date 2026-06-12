---
title: "Can't get sane to recognize scanner"
date: 2008-05-08
forum: Hardware
---

### Post by erikcw on 2008-05-08
Hi all,

I followed the instructions on this page to get my Fujitsu ScanSnap S510M working with Hardy.

[http://blog.psuter.ch/?p=58](http://blog.psuter.ch/?p=58)

I followed the directions, but can't seem to get sane to recognize the scanner.

Here is the output:
```

erik@turbo:~$ scanadf –help –device fujitsu:libusb:005:006
Usage: scanadf [OPTION]…
………SANE HELP INFO…….
scanadf: open of device fujitsu:libusb:005:006 failed: Invalid argument
Type “scanadf –help -d DEVICE'’ to get list of all options for DEVICE.

List of available devices:
v4l:/dev/video0
erik@turbo:~$ scanadf –device fujitsu:libusb:005:006 –source “ADF Duplex” –mode Color -v –resolution 150 –y-resolution 150
scanadf: open of device fujitsu:libusb:005:006 failed: Invalid argument
erik@turbo:~$

Here is my lsusb:
erik@turbo:~$ lsusb
Bus 005 Device 006: ID 04c5:116f Fujitsu, Ltd
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 009: ID 03f0:1424 Hewlett-Packard f2105 Monitor Hub
Bus 002 Device 008: ID 0471:0815 Philips
Bus 002 Device 007: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:0b0c Hewlett-Packard
Bus 001 Device 001: ID 0000:0000

And the bottom of my /etc/sane.d/fujitsu.conf
#scansnap S510
usb 0×04c5 0×1155

#scansnap S510M (added by Erik)
usb 0×04c5 0×116f

```

Thanks for your help!
Erik

---

### Post by flamacue on 2008-08-30
Maybe these will help..?

[color=blue]_[http://www.awe.com/mark/blog/200709161530.html](http://www.awe.com/mark/blog/200709161530.html)_[/color]
[color=blue]_[http://ubuntuforums.org/showthread.php?t=895209](http://ubuntuforums.org/showthread.php?t=895209)_[/color]

Those links speak to the S510 though, not the S510M.

I don't have one of these, so I can't really offer much assistance beyond this.  But, I am considering buying one (S510), so please post back here with your experiences.

---

### Post by Crafty Kisses on 2008-09-05
For scanners you can look through this list > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

