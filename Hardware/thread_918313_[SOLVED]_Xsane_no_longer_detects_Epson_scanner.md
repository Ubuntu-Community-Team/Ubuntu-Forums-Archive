---
title: "[SOLVED] Xsane no longer detects Epson scanner"
date: 2008-09-12
forum: Hardware
---

### Post by charonred on 2008-09-12
This started happening yesterday; Xsane no longer detects my Epson CX5300 scanner (printer is detected ok)

I've read a few posts and tried a couple of terminal scripts with the following results;

> **@**:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0808 [USB MFP]) at libusb:003:003
found USB scanner (vendor=0x046d, product=0x0928) at libusb:007:003
found USB scanner (vendor=0xeb1a, product=0x2860) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


**@**:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

note: the line 'product=0x0928)' actually reads 'product=0x0928' but it keeps getting turned into a smilie in this post.

How do I get Xsane to detect my scanner again?

---

### Post by charonred on 2008-09-13
bump

can't get xsane to work

---

### Post by charonred on 2008-09-18
Don't worry about it; after being without a scanner for the past week, xsane suddenly started working again.

There must have been a recent update package that fixed it :) though I would still like to know what went wrong and how I could've manually fixed it.

---

