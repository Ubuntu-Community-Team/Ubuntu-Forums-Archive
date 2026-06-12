---
title: "Simple Scan, XSane can't recognize Agfa 1212U Scanner on Ubuntu 14.04"
date: 2015-02-22
forum: Hardware
---

### Post by suaf on 2015-02-22
Hi all, 

I have an old Agfa Snapscan 1212U scanner, used it for years with Ubuntu, but since I installed 14.04, Simple Scan says ``unable to connect to scanner''. Xsane says ``No devices available''.

Interestingly enough, I have another laptop with 14.04 which uses the same scanner without any problems (both Acers).

lsusb shows the scanner: 

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c32 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 06bd:2061 AGFA-Gevaert NV SnapScan 1212U (?)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And so does sane-find-scanner:

```
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1bcf/0x2c32 at 001:003: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
found USB scanner (vendor=0x06bd [AGFA], product=0x2061 [ Snapscan1212u_2]) at libusb:003:003
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)

```

However, scanimage -L says ``No scanners were identified.''

I tried this popular solution, actually this is how it worked up to now, but now it had no effect: 
     [I]Copy the file SnapScan1212U_2.bin (as root) to:
     /usr/share/sane/snapscan/
     You will probably have to create the snapscan subdirctory.
     I ended up opening a konsole and navigated to my home directory where I'd used konqueror to copy and rename the file from the wine installation. I then typed this as root:
     cp SnapScan1212U_2.bin /usr/share/sane/snapscan/
     I believe you can sometimes use your file manager as root, so you might just find that easier if you have that option.
     Next, as root, modify /etc/sane.d/snapscan.conf
     You will find at the top, these two lines:
     # Change to the fully qualified filename of your firmware file, if
     # firmware upload is needed by the scanner
     Underneath this, change the line to:
     firmware /usr/share/sane/snapscan/SnapScan1212U_2.bin[/I]

---

### Post by vangli on 2015-04-23
Hi there

I got the exact same problem on my PC. I had the scanner running on 14.04, and the next week it didn't. First I thought it was an update which corrupted my working setup. I was wrong. After some testing, I remembered I have moved the USB cable from an USB 2.0 to an USB 3.0 port. The very strange thing is that you are able to detect your scanner one time when connected to an USB 3.0 port, and then it blocks. Because of this detection I thought all was ok. How wrong I was. The simple sollution, move your USB cable to an USB 2.0 connector, and it works. Of course you need to do the magic with firmware upload in the config file, but that have you already done

Best regards Bent

---

### Post by davidvandoren on 2015-04-24
Restart your pc and go into your bios.
Enable advanced settings and look for usb settings.
Change the USB 3.0 from XHCI enabled to disabled.
And if available the usb 2 settings EHCI settings from enabled to disabled or vise verse.

---

