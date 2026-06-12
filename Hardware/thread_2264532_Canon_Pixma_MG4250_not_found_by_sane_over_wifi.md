---
title: "Canon Pixma MG4250 not found by sane over wifi"
date: 2015-02-08
forum: Hardware
---

### Post by Wim De Winter on 2015-02-08
Canon Pixma MG4250 is not found by sane over wifi. The scanner is found however by ScanGearMP, a package by canon, and can be used.

I run kubuntu 14.04 LTS. I downloaded and installed both > MG4200 series ScanGear MP Ver. 2.00 for Linux (debian Packagearchive)
 and > MG4200 series IJ Printer Driver Ver. 3.80 for Linux (debian Packagearchive)
My settings so far:

The location of the scanner is mentioned in pixma.conf:```
bjnp://192.168.1.44
```

The location of the scanner is mentioned in net.conf:```
localhost
192.168.1.44
```

pixma and net are mentioned in dll.conf:```
pixma
net
```

in etc/services I have ```
sane-port    6566/tcp    sane saned    # SANE network scanner daemon
```

When I run ```
nmap -sL 192.168.1.*
``` the scanner/printer doesn't show up

What am I missing or doing wrong? As mentioned above, the scanner works flawlessly using the canon ScanGearMP, but not in SANE

---

### Post by aikishugyo on 2015-02-09
There are two things to worry about here as far as I can see:
1. If the scanner works in SANE with USB connection, then there is no problem with SANE
2. To use WiFi, there is another protocol, SANE over WiFi or something like that, which could have errors, but this is a separate issue from SANE.

Your best best would be to go to the SANE mailing lists and try for help there.

---

### Post by Wim De Winter on 2015-02-09
I'll look into that. Thaks for the reply!

---

### Post by pdc on 2015-02-09
so ScanGearMP is what Canon provide to run the scanner; and in contrast, sane is the open-source project for scanning support in linux;

from their list, your MG4200series device should be supported [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) (one assumes using usb); and so some might suggest adding the latest sane to your system

[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

Rolf maintains this ppa for the latest version of sane

this thread [http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=rolf+bensch](http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=rolf+bensch) shows someone recommending this

---

### Post by Wim De Winter on 2015-02-10
> **pdc said:**
> so ScanGearMP is what Canon provide to run the scanner; and in contrast, sane is the open-source project for scanning support in linux;

from their list, your MG4200series device should be supported [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) (one assumes using usb); and so some might suggest adding the latest sane to your system

[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

Rolf maintains this ppa for the latest version of sane

this thread [http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=rolf+bensch](http://ubuntuforums.org/showthread.php?t=2261650&page=2&highlight=rolf+bensch) shows someone recommending this

Thanks for the reply. Tested connecting with a USB, sane didn't work, ScanGearMP still does work, so probably sane issue? Will try the Rolf Bensch ppa.

---

### Post by Wim De Winter on 2015-02-10
Using the Rolf Bensch ppa solves the issue! THANKS the both of you for your input

---

### Post by pdc on 2015-02-10
> Using the Rolf Bensch ppa solves the issue!  .............great!! Thanks for keeping us updated.................all those hours Rolf spends slaving away are not wasted!

---

### Post by 4all on 2016-01-03
Great work Rolf

work out-of-the-box for me too on LinuxMint 17.3 and your PPA, printing & scanning

---

