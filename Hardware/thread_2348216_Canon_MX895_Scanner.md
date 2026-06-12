---
title: "Canon MX895 Scanner"
date: 2017-01-01
forum: Hardware
---

### Post by sugarat2 on 2017-01-01
Hi there, 

 I have just installed the current version (16.10) of Ubuntu Gnome and am trying to get my Canon MX895 multifunction printer working - the scanner part to be precise.  This has proved possible with previous Linux incarnations and I have recently gotten one working on Fedora with no issues.  Alas, so far I have not been successful with Ubuntu though. 

The Linux driver is available, but it expects libpng-12-0 and libusb-0.1-4.  These packages do not seem to be available for Ubuntu 16.10 as they are now quite old.   I have downloaded them for previous Ubuntu releases and installed them, and that made the install script for the driver happy, but when I run the scangearmp program now, it tries to detect the scanner and then fails, saying that no scanners could be found. 

So, my question is - what next to get the scanner working on Ubuntu 16.10 ? 

 Many thanks.

---

### Post by sugarat2 on 2017-01-01
Update:  It looks like perhaps the Canon files are not required, as Sane has a native Pixma backend which should support this scanner. 

After rebooting the scanner, I have found that the scan program (xsane) is now detecting the scanner on the network (it's wi-fi, not usb).   When I attempt to scan, the process starts, and I even see the previous of the scanned page begin to appear on the screen.  Unfortunately, after a few seconds the process comes to a screeching halt and a box pops up saying 'I/O error'.  The console window from wher I launched xsane shows the following:

```

[bjnp] bjnp_recv_data: ERROR - could not read response payload (select timed out)!

```

It seems that the Sane backend is not quite able to communicate with the scanner. 

Any ideas? 

I've had this working perfectly on Fedora 25, so I'd hate the Ubuntu Gnome distro to not be able to also pull of this feat!

---

