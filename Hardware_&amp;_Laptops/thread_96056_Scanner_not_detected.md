---
title: "Scanner not detected"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by Insane on 2005-11-28
well, at least I dont know how t scan with my CanoScan LLide 500F

Can anyone help?

---

### Post by _4ace on 2005-11-28
try typing in a terminal

scanimage -L

then try to start xsane. that was all i had to do to set up my scanner, which is a canon lide 30. it needs to be supported though.

---

### Post by Insane on 2005-11-28
This is what happened when i did that:

```
andre@ubuntu:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

andre@ubuntu:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04a9, product=0x221f, chip=GL841?) at libusb:005:003  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by ChrisTheGeek on 2005-12-01
Could be a permissions problem.  Try running the following commands and post back the output:

sudo sane-find-scanner -q

sudo scanimage -L

Update: sorry, I've just checked the sane website here:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=Lide+500F&bus=usb](http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=Lide+500F&bus=usb)

And your scanner is not yet supported.  You'll have to wait until somebody has written a driver for it - when they have you can update your 'genesys' driver from the sane website and it should work.   You can check the sane development list to see what progress is being made on a driver.

---

