---
title: "sane scanner recognition"
date: 2010-09-08
forum: Hardware
---

### Post by qsecofer on 2010-09-08
I have installed sane and sane-utils on an Ubuntu server (32 bit) system.
sane-find-scanner finds my scanner but scanimage -L doesn't

and now i am stuck tried search the web but not really sure what to look for and where to start.
any help pushing me in the right direction would be great.


If i run sudo sane-find-scanner I get the following 


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x2404 [Deskjet F2200 series]) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

which indeed finds my scanner (allin-one)

if i run sudo scanimage -L I get

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by chideock on 2010-10-18
gsecofer

I get the info for my scsi Nikon super coolscan 4000.

Hoping someone has an answer

---

### Post by chideock on 2010-10-18
got mine working

---

