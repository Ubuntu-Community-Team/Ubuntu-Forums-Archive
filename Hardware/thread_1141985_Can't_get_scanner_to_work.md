---
title: "Can't get scanner to work"
date: 2009-04-28
forum: Hardware
---

### Post by Regenerate on 2009-04-28
I have a Plustek ScanCopy 115 and trying to get it to work with xsane.

*sudo sane-find-scanner* returns this:
>  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x046d [OEM], product=0x0896 [Camera]) at libusb:001:003
found USB scanner (vendor=0x07b3 [PLUSTK INC], product=0x081c [URB2.0 SCANNER], chip=GL841?) at libusb:005:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
So the plustek scanners is found at libusb:005:007 (the other one is the laptops internal camera).

Then I try *sudo scanimage -L* but that returns:
> device `v4l:/dev/video0' is a Noname Camera virtual device
So no sign of the plustek scanner here.

So now what do I do? [http://www.howtoforge.com/sane_xsane_scanner](http://www.howtoforge.com/sane_xsane_scanner) wasn't really helpful for me.

---

### Post by desertdog on 2009-04-29
This scanner is not supported by Sane. (Xsane is just a graphical user interface for Sane). 

[http://www.sane-project.org/unsupported/plustek-scancopy-115.html](http://www.sane-project.org/unsupported/plustek-scancopy-115.html)

This scanner could be added to the genesys backend of sane, but this probably won't happen until someone with your scanner and programming abilities does the work.

In the meantime, you could dual boot with windows to do your scanning or set up a virtual machine running windows to do your scanning.

---

### Post by Regenerate on 2009-04-29
Thanks for the reply. I already have a virtualbox with windows running but I can't get the scanner to work properly (works fine on a normal windows installation), so I thought I might try getting it to work with Ubuntu. To bad, guess this means I'll need a new scanner...

---

