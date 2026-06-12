---
title: "Scanner Driver"
date: 2010-11-26
forum: Hardware
---

### Post by pieroxy on 2010-11-26
I just bought a Scanner from Mustek which is called "PageExpress A3 USB Pro" or so the box says. On the website I bought it it is labelled ScanExpress and not PageExpress.

I am running Ubuntu 10.04 and I have issues with making the thing work with it.

Here is what I tried:


```
pieroxy@pieroxy-linux:~/progs/bin$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).



pieroxy@pieroxy-linux:~/progs/bin$ sudo sane-find-scanner
[sudo] password for pieroxy: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x055f [Hewlett-Packard.        ], product=0x040b [USB2.0 Scanner            ], chip=SQ113) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

So now my question is: What is the next step? Can I use it?

If not, can I use the Windows drivers in any way or shape under linux?

---

