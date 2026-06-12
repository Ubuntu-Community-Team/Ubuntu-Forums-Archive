---
title: "How to install Epson Perfection 3490 photo scanner"
date: 2014-02-21
forum: Hardware
---

### Post by satimis on 2014-02-21
Hi all,

Ubuntu 12.04 64bit

$ sane-find-scanner```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:002:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

$ apt-cache policy xsane```

xsane:
  Installed: 0.998-3ubuntu2
  Candidate: 0.998-3ubuntu2
  Version table:
 *** 0.998-3ubuntu2 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Already installed

Simple scan can't find it - Unable to connect to scanner

Found following link;
Ubuntu Scanner Epson Perfection 3490 Photo
[http://www.serkey.com/ubuntu-scanner-epson-perfection-3490-photo-be87ca.html](http://www.serkey.com/ubuntu-scanner-epson-perfection-3490-photo-be87ca.html)

/etc/sane.d/snapscan.conf```

...
# Epson Perfection 3490
usb 0x04b8 0x0122
...

```
already there.

```

- I changed the permissions for the files in /proc/bus/usb/001/ to enable read/writing for group and other
```
/proc/bus/usb: No such file or directory

Please help.  Thanks

satimis

---

