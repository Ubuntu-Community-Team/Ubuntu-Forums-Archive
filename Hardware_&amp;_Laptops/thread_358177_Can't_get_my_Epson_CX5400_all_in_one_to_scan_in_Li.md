---
title: "Can't get my Epson CX5400 all in one to scan in Linux"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Wooksta on 2007-02-10
Hi All,

I'm still pretty new to Ubuntu and this is officially my first post on the forums so I'll try and not cause to much of a headache.

I'm stuck trying to get my Epson CX5400 all in one printer/scanner/copier to work with sane for scanning documents.  The printer works fine but I've had no luck with scanning at all.

"sane-find-scanner" produces the following output

```
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0808 [USB MFP]) at libusb:002:016
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Although when I try "scanimage -L" I get the following:

```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

I've tried this as root as well and get the same error so it doesn't seem to be an issue with permissions.

I have also added the line
```
usb 0x04b8 0x0808
```
to my /etc/sane.d/epson.conf but it still hasn't worked.

The device shows up in lsusb as well so the system appears to see it fine...

```
Bus 002 Device 016: ID 04b8:0808 Seiko Epson Corp.
```

I was following this tutorial [http://ubuntuforums.org/showthread.php?t=316961](http://ubuntuforums.org/showthread.php?t=316961) (changing the appropriate info for my printer) but have had no luck yet.

If anyone could help me out with this it would be much appreciated. I saw the same problem when I was playing around with Fedora before I moved to Ubuntu (been a great choice so far :)).

If you want more info just leave me a note and I'll post it asap.

Thanks in advance.  :)

---

