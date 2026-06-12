---
title: "Xsane: failed to start scanner - invalid argument"
date: 2021-12-08
forum: Hardware
---

### Post by knight69 on 2021-12-08
This problem has been around a long time, but I still haven't solved it. 

I have a Lexmark CX317DN laser printer/scanner connected via USB to my desktop computer running Ubuntu 20.04.3 with gnome 3.36.8. I am also running gnome flashback with compiz.

When I launch xsane, it recognizes the Lexmark device, but when I click on the scan button I get the message: "Failed to start scanner: invalid argument". The printer works perfectly with all applications and the scanner works perfectly with simple-scan.

dmesg gives the following:[INDENT][ 6041.528898] usb 1-2: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
[ 6046.530148] usblp1: removed
[ 6046.655839] usb 1-2: reset high-speed USB device number 9 using xhci_hcd
[ 6046.813717] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 9 if 1 alt 0 proto 2 vid 0x043D pid 0x022F
[/INDENT]
scanimage -T [INDENT]$ scanimage -T
Output format is not set, using pnm as a default.
scanimage: scanning image of size 1275x1650 pixels at 1 bits/pixel
scanimage: acquiring gray frame, 1 bits/sample
scanimage: reading one scanline, 160 bytes...    PASS
scanimage: reading one byte...        PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...     PASS
scanimage: stepped read, 32 bytes...     PASS
scanimage: stepped read, 64 bytes...     PASS
scanimage: stepped read, 128 bytes...     PASS
scanimage: stepped read, 256 bytes...     PASS
scanimage: stepped read, 255 bytes...     PASS
scanimage: stepped read, 127 bytes...     PASS
scanimage: stepped read, 63 bytes...     PASS
scanimage: stepped read, 31 bytes...     PASS
scanimage: stepped read, 15 bytes...     PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS
[/INDENT]
scanimage -L[INDENT]scanimage -L
device `lexmark_nscan:libusb/001/009' is a Lexmark Lexmark CX317dn Scanner
device `lexmark_nscan:libnet/SPECIFY_DEVICE' is a Lexmark Network Scanner
device `escl:[https://192.168.1.252:443](https://192.168.1.252:443)' is a ESCL EPSON XP-440 Series SSL flatbed scanner
device `escl:[http://192.168.1.252:443](http://192.168.1.252:443)' is a ESCL EPSON XP-440 Series flatbed scanner
device `epson2:net:192.168.1.252' is a Epson PID 1114 flatbed scanner[/INDENT]

Launching xsane from the command line gives the following message:[INDENT]$ xsane
Gtk-Message: 22:36:43.016: Failed to load module "canberra-gtk-module"
(xsane:6822): Gdk-CRITICAL **: 22:36:56.427: IA__gdk_drawable_unref: assertion 'GDK_IS_DRAWABLE (drawable)' failed
(xsane:6822): Gdk-CRITICAL **: 22:36:56.427: IA__gdk_drawable_unref: assertion 'GDK_IS_DRAWABLE (drawable)' failed
[/INDENT]

I have run out of ideas and hope that someone can help with this problem.

---

