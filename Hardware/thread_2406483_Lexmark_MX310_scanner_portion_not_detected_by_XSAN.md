---
title: "Lexmark MX310 scanner portion not detected by XSANE"
date: 2018-11-21
forum: Hardware
---

### Post by Rafu on 2018-11-21
I’m running Ubuntu Mate 16.04 on all my computers. I have this multifunction laser printer from Lexmark, including a scanner, but I haven’t been using the scanner in ages - probably not since I’ve been running 16.04
Now I urgently need to get a pile of paperwork scanned, and I’ve realized it doesn’t work at all. While the printer works just OK - connected via USB cable - neither Simple Scan nor XSANE manage to detect the scanner as such. They tell me there’s no device connected they can use.
I tried installing [this driver ]([http://support.lexmark.com/index?docLocale=en_US&amp;page=content&amp;segType=recommendedSegmentOS&amp;id=DR23974&amp;locale=EN&amp;userlocale=EN_US#](http://support.lexmark.com/index?docLocale=en_US&amp;page=content&amp;segType=recommendedSegmentOS&amp;id=DR23974&amp;locale=EN&amp;userlocale=EN_US#)) from Lexmark, which appeared to be the closest match: it doesn’t seem to make any difference.

Lexmark tech support pointed me at SANE documentation, but I’ll confess feeling quite lost in it.

When I run XSANE it says “no devices available”. Running it as root user, same result (after the scare dialog).

This is the output for same-find-scanner, as a regular user and then as root:

> ```
[INDENT] rafu@Anatrone:~$ sane-find-scanner
 # sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.
 # No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.
 could not open USB device 0x8087/0x0020 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x275d/0x0ba6 at 001:003: Access denied (insufficient permissions)
found USB scanner (vendor=0x043d [Lexmark], product=0x0227 [Lexmark MX310dn]) at libusb:001:004
could not open USB device 0x8087/0x0020 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend’s manpage.
 # Not checking for parallel port scanners.
# Most Scanners connected to the parallel port or other proprietary ports
# can’t be detected by this program.
 # You may want to run this program as root to find all devices. Once you
# found the scanner devices, be sure to adjust access permissions as
# necessary.
 [/INDENT]

```

> ```
[INDENT] rafu@Anatrone:~$ sudo sane-find-scanner
[sudo] password for rafu:
 # sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.
 # No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.
 found USB scanner (vendor=0x043d [Lexmark], product=0x0227 [Lexmark MX310dn]) at libusb:001:004
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend’s manpage.
 # Not checking for parallel port scanners.
 # Most Scanners connected to the parallel port or other proprietary ports
# can’t be detected by this program.
 [/INDENT]

```

Any idea what else I could try?

---

### Post by him610 on 2018-11-22
As suggested, did you try...? ```
scanimage -L 
```

You also did not indicate which drivers you downloaded and installed.
RE: [http://support.lexmark.com/index?page=driversdownloads&linkSelected=node2%5Esubnode2&locale=EN&userlocale=EN_US]("http://support.lexmark.com/index?page=driversdownloads&linkSelected=node2%5Esubnode2&locale=EN&userlocale=EN_US")

I found these drivers on referenced page,

---

