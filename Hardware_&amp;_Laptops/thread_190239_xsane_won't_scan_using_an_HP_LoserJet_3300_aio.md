---
title: "xsane won't scan using an HP LoserJet 3300 aio"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by lazylawyer on 2006-06-06
I have an HP LaserJet 3300 aio connected via USB.  I'm running Dapper Drake (love it).

XSane won't scan.  It reports: "Failed to start scanner: Document feeder out of documents".  There is no document feeder on this scanner.  (I never tried this in Breezy, but [this post]("http://ubuntuforums.org/showthread.php?t=148017&highlight=sane+document+feeder") suggests I should have.


scanimage reports the correct device family, but gives the same error message.  How do I persuade it that there's no document feeder?

henry@ubuntu:~$ scanimage -L
device `hpaio:/usb/HP_LaserJet_3300_3310_3320?device=/dev/usblp0' is a hp HP_LaserJet_3300_3310_3320 multi-function peripheral
henry@ubuntu:~$ scanimage >tmp.pnm
scanimage: sane_start: Document feeder out of documents
henry@ubuntu:~$

---

### Post by banksw on 2006-06-06
I have an HP officejet T45xi and it can not scan either.  Nor does it find the scanimage -L in Bash that you used.  Also i note that only flatbed scan option shows but i have a auto doc feeder.  Also get the scanner is busy msg.  Hope someone can add additional info.  new to linux.

---

### Post by JeffreyRatcliffe on 2006-06-10
I have an OfficeJet5500 which worked perfectly under Breezy as the default device. After some time thinking it wasn't working at all, I now see that I have to specify the device:

```
$ scanimage --list-devices
device `v4l:/dev/video1' is a Noname UNKNOWN/GENERIC virtual device
device `v4l:/dev/video0' is a Noname UNKNOWN/GENERIC virtual device
device `hpaio:/usb/officejet_5500_series?serial=MY42QF209H96' is a hp officejet_5500_series multi-function peripheral
$ scanimage > test
```

nothing happens

```
scanimage --device hpaio:/usb/officejet_5500_series?serial=MY42QF209H96 > test
```

bingo!

Any ideas how I specify it as the default device?

Jeff

---

### Post by JeffreyRatcliffe on 2006-06-12
And the answer was, of course, that Google was my friend:

```
export SANE_DEFAULT_DEVICE=hpaio:/usb/officejet_5500_series?serial=MY42QF209H96
```

---

