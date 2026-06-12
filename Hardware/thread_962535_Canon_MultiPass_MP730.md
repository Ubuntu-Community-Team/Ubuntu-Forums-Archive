---
title: "Canon MultiPass MP730"
date: 2008-10-29
forum: Hardware
---

### Post by tonyh6243 on 2008-10-29
I have one item left that is preventing me from removing my windows partition. Ubuntu Hardy 8.04 managed to recognize my Canon MultiPass MP730 without a problem. The one remaining cheviot I have is getting the scanning function to work on this multifunction printer. Every time I try to scan something I receive the message of:
> Unknown message: scanimage: sane_read: Error during device I/O

And:

> Unknown message: Scanned page 1. (scanner status = 9)

I have tried scanning through multiple programs such as:

Gimp
Openoffice
gscan2pdf

I am not sure what my next step should be.

---

### Post by tonyh6243 on 2008-10-31
Does anyone have any suggestions?

---

### Post by skyshock21 on 2008-11-18
I'm in the same boat.  Some more info:

```
$ scanimage --list-devices
device `pixma:04A9262F_000000014BD3' is a CANON Canon MultiPASS MP730 multi-function peripheral

```

Okay, so the scanner is there...

```
$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon Inc.], product=0x262f [MP730]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

Showing USB location....

```
$ scanimage -d pixma:04A9262F_000000014BD3
P6
# SANE data follows
637 868
255
scanimage: sane_read: Error during device I/O

```

wtf.

```
$ scanimage -T
scanimage: scanning image of size 637x868 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1911 bytes...	FAIL Error: Error during device I/O

```

again, wtf.  The MP730's all-in-one printer works fine (shot out a test page), but scanning doesn't.  It's not a faulty USB cable either.  Anyone have a clue what's going on?  I get the same message outputted via GUI when i use XSane as well.

---

### Post by waddles on 2009-04-26
I have been spending a lot of time working through the problems in the MP730 driver. Please take a look at my page at [http://waddles.org/content/sane-canon-mp730-driver](http://waddles.org/content/sane-canon-mp730-driver)

Unfortunately, most of the fixes will probably not make it into CVS before S.A.N.E 1.0.20 is released so you will need to apply the patches yourself.

---

