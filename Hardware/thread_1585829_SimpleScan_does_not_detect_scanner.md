---
title: "SimpleScan does not detect scanner"
date: 2010-10-01
forum: Hardware
---

### Post by owen_cook on 2010-10-01
Using a beta of 10.10, SimpleScan does not detect my ancient Scanmaker-X6

My Ubuntu-9.04 with xsane etc installed happily works with the Scanmaster

Installed xsane etc on 10.10 beta, and still no hardware detection.

I would like to know if there has been some radical change to the database that allowed the ScanMaster to be used on 9.04 (sane) but not on SimpleScan


TIA

---

### Post by IcarusR on 2010-10-01
The SANE supported devices says your scanner is supported in the latest stable version sane-backends-1.0.21.
The backend for this scanner, sane-microtek2, is no longer maintained. So it is not likely that your scanner has been removed.

Check that sane, libsane & sane-utils  are installed.

Run the following to see if your scanner is found

```
sane-find-scanner
```
```
scanimage -L
```

Just noticed you are running 10.10beta, maybe better to post on dev board ?

[http://ubuntuforums.org/forumdisplay.php?f=385]("http://ubuntuforums.org/forumdisplay.php?f=385")

---

