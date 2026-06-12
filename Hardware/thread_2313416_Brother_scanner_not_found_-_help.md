---
title: "Brother scanner not found - help"
date: 2016-02-12
forum: Hardware
---

### Post by wgarider2 on 2016-02-12
looking for some help with a Brother DCP-7020 printer/scanner - printing works with no issues but darned if I can get scanning to work. I've searched and read through many posts here and still can't get things to work. Appreciate any help or experience others may have had. I've tried xsane scanning tool, gscan2pdf & simple scan with no success.

Relevant info:
Ubuntu 15.10

**mypc@mypc:~$ lsusb**
Bus 002 Device 007: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 006: ID 04e8:1f02 Samsung Electronics Co., Ltd 
Bus 002 Device 008: ID 04f9:0183 Brother Industries, Ltd DCP-7020

**mypc@mypc:~$ dpkg -l | grep Brother**
ii  brscan-skey 0.2.4-1 amd64 Brother Linux scanner S-KEY tool
ii  brscan2 0.2.5-1 amd64 Brother Scanner Driver
ii  printer-driver-brlaser 3-3build1 amd64 printer driver for (some) Brother laser printers
ii  printer-driver-ptouch 1.3-8ubuntu1 amd64 printer driver Brother P-touch label printers

**mypc@mypc:~$ sane-find-scanner**
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

*found USB scanner (vendor=0x04f9, product=0x0183) at libusb:002:008*
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

**mypc@mypc:~$ scanimage -L**
No scanners were identified...............


(device info I put in libsane.rules)
**mypc@mypc:~$ sudo gedit 40-libsane.rules**
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

---

### Post by Vladlenin5000 on 2016-02-12
Hi and welcome.

This is not new but should explain why the scanner requires additional steps and provide a solution: [http://dullsharpness.com/2013/08/31/install-brother-dcp-7020-printer-on-debian-or-ubuntu/](http://dullsharpness.com/2013/08/31/install-brother-dcp-7020-printer-on-debian-or-ubuntu/)

---

### Post by eezacque on 2016-02-19
I have had issues getting my Canoscan Lide 25 to work with Ubuntu. Disabling xHCI in BIOS worked for me, and recently, I found that the scanner has stopped working since kernel upgrade 3.19.0-44. I know, it is a different scanner, but is doesn't hurt to try...

---

