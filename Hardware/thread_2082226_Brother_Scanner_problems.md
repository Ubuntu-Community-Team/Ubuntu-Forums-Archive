---
title: "Brother Scanner problems"
date: 2012-11-08
forum: Hardware
---

### Post by stevebateman63 on 2012-11-08
Hiya all
Just installed my Brother MFC640CW using the MFC210 deb files. Printer is working fine but my scanner comes up with "failed to open device:Brother2,bus1,dev1: invalid argument when starting Xsane. Its a local printer on usb.. Any help would be great thanks . sane seems to find 2 scanners ...
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0197) at libusb:005:003
found USB scanner (vendor=0x0ac8, product=0x305b) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

### Post by gifford on 2012-11-08
Go to the Brother site for linux drivers and follow the instructions given for your particular model. 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

You will have to install the appropriate brscan file for your device and follow the detailed instructions.

In my experience it has always been easier and less frustrating to rely on the Brother instructions to set up my multi purpose devices.

---

### Post by kurt18947 on 2012-11-09
There are two issues I've run into installing Brother scanners.  One has to do with a flaw in I believe alien that appears on 64 bit systems.  The other is non-SUDO user permission problem.  Both are documented on Brother's site.

Fix for 64 bit problem:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

To be able to scan as a non-SUDO user

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6)

---

### Post by stevebateman63 on 2012-11-09
Thanks Kurt all have tried as they say on the brother website No luck
I cant even scan as sudo I will try a full reinstall I think.
I think its not finding the device . Strange as simple scan finds the device but can't use it
Where xsane just errors before starting

---

