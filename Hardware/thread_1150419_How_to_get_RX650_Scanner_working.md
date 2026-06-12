---
title: "How to get RX650 Scanner working?"
date: 2009-05-06
forum: Hardware
---

### Post by gwmbox on 2009-05-06
Hi all

Has anyone been able to get an Epson RX650 scanner working?  I have the printer part working ok but I am having issues with scanner.  SANE does not recognise it, I have installed libsane and libsane-extras and tried to get it working but no luck (so far).

I downloaded the driver from [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) for my x64 by downloading the DEB file for the scanner (iscan_2.19.0-4_amd64.deb) but it comes up with a libltdl3 dependency error when trying to install.  I then went to see if I could get that package to install via the Synaptic Package Manager but it has libltdl7 and not libltdl3 available - the 3 is obviously and old one???  I installed libltdl7 as well as the libltdl-dev but still no luck, SANE can still not recognise the scanner.

Please help me get my scanner working :)

EDIT:  Had an auto update overnight and this morning all is work - sweet - thanks all :)

---

### Post by 666porcondissaum on 2009-05-07
How many nights am I supposed to wait to get it working?!??! Help! Actually no successful updates for this issue.

---

### Post by toogooda on 2010-03-16
I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php]("http://avasys.jp/eng/linux_driver/faq/id000613.php")

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/en/hardy/i386/libltdl3/download")

64-Bit = [http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download]("http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download")

All working in xsane for me now, hope it helps

AT

---

