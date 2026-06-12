---
title: "Aaargh - Scanjet scanner broken in dapper"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by jonboy99 on 2006-08-04
So frustrating - HP scanjet 3300C, worked fine in breezy but now not recognised in dapper, even as root.

xsane just opens and closes so quickly I can't read the error message, and doesn't leave any errors when opened from terminal.

Have tried sane-find scanner and scanimage -L, as follows:

```
jonboy99@xp24ubuntu:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0205 [HP ScanJet 3 300C]) at libusb:003:002
found USB scanner (vendor=0x066f, product=0x4200) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
jonboy99@xp24ubuntu:~$ scanimage -L
jonboy99@xp24ubuntu:~$ sudo scanimage -L
jonboy99@xp24ubuntu:~$

```

I hate the thought of going back to windows, would rather buy a new scanner, but lots seem to be broken in dapper, and don't know of any up to date hardware compatibility lists for dapper.

---

### Post by rbmorse on 2006-08-04
You scanner is listed as supported.  You need the SANE-niash backend. I don't know what that means, but that's what SANE says.

---

### Post by zxee on 2006-08-05
See what modules are loading on your system? > lsmod
Maybe you can upgrade sane/xsane-but if that doesn't bring the correct driver/sane backend into your system you will need to go to the sane site and look at how to load the correct backend for your scanner.

---

