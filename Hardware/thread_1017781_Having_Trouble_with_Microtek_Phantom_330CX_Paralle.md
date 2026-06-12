---
title: "Having Trouble with Microtek Phantom 330CX Parallel Port Scanner"
date: 2008-12-21
forum: Hardware
---

### Post by Erwin Criddle on 2008-12-21
Hi,
I have a Microtek Phantom 330CX Scanner (Parallel Port) which I cannot seem to get working in Ubuntu 8.10.
I looked up the sane device database and it says that the Microtek Phantom 330CX is supported.

When I run "scanimage -L", I get this output:
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
This is the same in root or normal user.

When I run "sane-find-scanner", I get this output: (Normal User)
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x1385, product=0x5f01) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
Root User:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x1385 [Atheros Communications Inc], product=0x5f01 [WPN111]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

Any ideas?? :confused:

---

### Post by Banjouser on 2009-05-24
I understand you very good and feel sympathy for the situation
As a matter of fact I have the same problem and have no idea how to solve it.
Therefore I ask for help too.
Help will be appreciated.
Expecting some answers.
Greetings from Serbia!

---

### Post by Erwin Criddle on 2009-05-25
Thank-you for assuring me that I am not the only person having this problem.
I will keep looking for a solution to this problem and if I do find one, then I will post it here in full detail.
However, at the moment that does not seem to be very promising as I have only had one reply (you).

---

### Post by simonrodan on 2012-06-12
I have the same questions - nothign I have found yet has solved the problem. 

Any guidance woudl be greatly apprecaited.

---

