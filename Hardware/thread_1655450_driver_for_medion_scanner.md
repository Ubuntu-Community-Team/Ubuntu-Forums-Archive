---
title: "driver for medion scanner"
date: 2010-12-29
forum: Hardware
---

### Post by The_Philosophist on 2010-12-29
Hi, 

I have a medion scanner and want to use it on ubuntu, when I plug the device in nothing happens.
When I run lsusb
I see the device is called: Primax Electronics, Ltd Medion MD 6190 Scanner
Using these 2 guides I figured some things out:
[https://help.ubuntu.com/community/ScanningHowTo#Manually](https://help.ubuntu.com/community/ScanningHowTo#Manually) installing a scanner
[https://help.ubuntu.com/10.04/printing/C/scanning.html](https://help.ubuntu.com/10.04/printing/C/scanning.html)
BUT I have no clue wich driver I should use for this scanner, can anyone help me with this or point a please where I could start looking myself as I have no clue where I should start looking.

PS: I ran sane-find-scanner and that also detected the scanner but scanimage -L returns the following:
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

---

### Post by IcarusR on 2010-12-29
Your scanner is unsupported, there is no driver for it, see here

[http://www.sane-project.org/sane-mfgs.html#Z-MEDION-LIFETEC-TEVION-CYTRON]("http://www.sane-project.org/sane-mfgs.html#Z-MEDION-LIFETEC-TEVION-CYTRON")

& 

[http://www.sane-project.org/unsupported/medion-md6190.html]("http://www.sane-project.org/unsupported/medion-md6190.html")

---

