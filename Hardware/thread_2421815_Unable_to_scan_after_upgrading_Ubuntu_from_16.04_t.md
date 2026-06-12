---
title: "Unable to scan after upgrading Ubuntu from 16.04 to 18.04"
date: 2019-06-27
forum: Hardware
---

### Post by jj.wauters on 2019-06-27
The Samsung SCX-4200 can still print but refuse scanning. 
In Simple Scan I cannot select the Samsung SCX-4200 scanner. Instead the Samsung Orion scanner is proposed. This scanner is unknown to me.

Running ```
sudo sane-find-scanner
``` returns :
> 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:002
found USB scanner (vendor=0x138a, product=0x0050) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



I suppose "(vendor=0x138a, product=0x0050)" is referencing to that unwanted Orion.

Any idea how to proceed in order to solve?

---

### Post by brian_p on 2019-06-27
> Any idea how to proceed in order to solve? 

Most likely a bug in 18.04's libsane. See

[https://wiki.debian.org/Scanner#issue](https://wiki.debian.org/Scanner#issue)

for a solution.

Please, say how you go on.

---

