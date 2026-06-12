---
title: "parallel port scanner not recognized (plustek opticpro 9636t) - &quot;Not checking&quot;"
date: 2009-01-17
forum: Hardware
---

### Post by Kyosys on 2009-01-17
alright, I just got a Plustek OpticPro 9636T scanner, and I've been trying to get it to work. 

First, I saw if it was recognized:
```
$ scanimage --list-devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
it was not. So I did this:
```
$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

Now, here it says "Not checking for parallel port scanners.", but my Scanner USES the parallel port.


Help?

---

### Post by Kyosys on 2009-01-18
Since this thread is now on page 5, I think it's fair to bump it.

---

### Post by Malvazar on 2011-08-09
I'm having this exact same problem! Scanner model and everything. Could really use some insight on how to get the system to see the scanner.

---

### Post by Nhorning on 2011-12-18
Same here. Could use some help

---

