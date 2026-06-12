---
title: "Epson SX115"
date: 2009-11-29
forum: Hardware
---

### Post by sdd231163 on 2009-11-29
Anybody had an joy installing the drivers for this printer? I downloaded the driver script from [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) and ran the script. I have been left with a broken package looking for a dependancy (pips-debian4.0). I cannot purge the packages installed because one (pips-snx110) will not remove but returns an error. I therefore cannot upgrade the system as this error prevents it. Any advice would be appreciated.
I am using k/ubuntu 9.10.

---

### Post by koistinen on 2010-01-15
I also have the Epson SX115, and Ubuntu 9.10 (64-bit AMD X2).
Installing the printer (SX110 according to the installer) cause printing to work but the scanner can't be found.
After uninstalling the printer, installing the scanner driver and rebooting, Xsane finds the scanner and it works fine, but the printer won't be found until after I quit Xsane.
So, problem for me is: I have a multifunction printer but can only install one function at a time.
As it is rather slow, an acceptable soulution would be to have a meta-printer that accept print jobs and installs the printer driver when it is needed. I don't need the printer and scanner to work at exactly the same time, as long as the switch is automatic it would be ok for the prints to be blocked as long as the scanner is used.
Scanner driver from _[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)__ (select_ Ubuntu etc.)

---

### Post by dekinstoke on 2010-03-10
**Using Epson SX115 on Ubuntu 9.10, the scanner driver/software from Avasys (iscan) works perfectly and actually smoother than on Windows. But the printer is not recognized yet. Not a major problem for me as I have a working printer on system already.**

---

### Post by jalirious on 2011-02-01
chose sx110 for the printer in the system->admin->printing, works fine.

---

