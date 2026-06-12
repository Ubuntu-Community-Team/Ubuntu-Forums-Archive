---
title: "Canon Imageformula P-215 Scanner"
date: 2013-05-31
forum: Hardware
---

### Post by ulugeyik on 2013-05-31
Hello,

I can not get my Canon Imageformula P-215 working. I have seen various threads -- see below -- that appears to have solved the problem for a similar scanner, P-150, but they do not seem to work for this scanner. Any suggestions ? 

So far I have:

sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x1083, product=0x1646) at libusb:001:014
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

dmesg

[3984109.484017] usb 1-7: new high-speed USB device number 14 using ehci_hcd
[3984109.617439] usb 1-7: New USB device found, idVendor=1083, idProduct=1646
[3984109.617446] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[3984109.617449] usb 1-7: Product: CANON   P-215           
[3984109.617452] usb 1-7: Manufacturer: CANON   
[3984109.617454] usb 1-7: SerialNumber: FUA44340

Here is the thread with P-150

[http://ubuntuforums.org/showthread.php?t=1504656](http://ubuntuforums.org/showthread.php?t=1504656)

---

### Post by john_doe2 on 2013-08-29
Oh I'm sorry (and I wish I knew how to help).

I'm shopping for a portable Automatic Document Feed (ADF) Scanner and this model came up as ideal, but for Ubuntu compatibility.  Generally, I'm not finding much of any information about linux use on the portable ADF Scanners
I've looked on:
 

 [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)
 

 [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
 

 or on the manufacturers' specs.

This is type of scanner that would be really useful.  I'm considering ditching Microserf, but this scanner issue may require a partition (or other solution?).

Thanks.

---

