---
title: "Epson RX610 Scanner under Ubuntu 9.10"
date: 2010-03-15
forum: Hardware
---

### Post by toogooda on 2010-03-15
How Do I get the scanner for my RX610 multifunction working with Ubuntu 9.10.

It used to work with 9.4 but not working with 9.10.

I have installed libsane-extras but it made no difference, when I load xsane I just get "No devices Available"

Anything else I can try?

---

### Post by sisco311 on 2010-03-15
Try to install iscan:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by ellgor on 2010-03-15
Hi,

If Imagescan doesn't work for you try opening a terminal and starting xsane (or Imagescan) from there :

sudo xsane

ignore the security warnings and continue, first time in years I've seen xsane run.

Regards, Ellgor.

---

### Post by toogooda on 2010-03-19
I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

above link seems to have changed to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php](http://avasys.jp/eng/linux_driver/faq/id000613.php)

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/...ltdl3/download](http://packages.ubuntu.com/en/hardy/...ltdl3/download)

64-Bit = [http://packages.ubuntu.com/en/hardy/...ltdl3/download](http://packages.ubuntu.com/en/hardy/...ltdl3/download)

All working in xsane for me now, hope it helps

---

