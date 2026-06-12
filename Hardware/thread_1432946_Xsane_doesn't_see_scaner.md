---
title: "Xsane doesn't see scaner"
date: 2010-03-18
forum: Hardware
---

### Post by vchapman on 2010-03-18
I have a Canon MP250 printer / scaner. Thanks to some help here I manage to get a Linux driver for the printer side from a Canon site in Australia.

Now I would like to capture images using Xsane. When I start up Xsane, it doesn't see the scanner. 

 sudo sane-find-scanner -p

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x173a [MP250 series]) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

So you can see that there is a scanner on the usb port.

What do I need to do to make the connection.

TIA

---

### Post by ellgor on 2010-03-18
Hi,

Try starting xsane from a terminal :

sudo xsane

ignore the warning message, worked for me.

Regards, Ellgor.

---

### Post by vchapman on 2010-03-18
I can't get past the warning message.

---

### Post by ellgor on 2010-03-19
Hi again.

Check in synaptic to see if libxsane-dev is installed, then try the procedure again.

Regards, Ellgor.

---

