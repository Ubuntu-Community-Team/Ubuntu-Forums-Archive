---
title: "scanner - Brother DCP-115C"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Murfy on 2006-06-15
Hello,

I bought myself a Brother DCP-115C, printing works perfectly, but I'm having difficulties installing the scanner.

I did what the Brother Linux manual said. When I run ```
sane-find-scanner -q
``` I get this:```
found USB scanner (vendor=0x04f9, product=0x0152) at libusb:004:004
found USB scanner (vendor=0x046d, product=0x08f5 [Camera]) at libusb:004:003
```That's ok so far, looks good.. the first scanner at libusb:004:004 is the Brother scanner according to lsusb. The camera is a Logitech Quickam Communicate.

Now, when I run Kooka, it asks me to select a scanner. The only option I get is the camera?

When I run ```
scanimage --help
``` it sais at the bottom:```
List of available devices:
    v4l:/dev/video0

```So where is the scanner?

Thanks in advance :)

---

### Post by zeekoe on 2007-09-02
I found this topic using google. For everyone finding a solution too, this was all I needed to do (for Feisty):

[LIST=1]
[*]Download brscan2 ([http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)) and dpkg --install it
[*]sudo apt-get install sane xsane kooka gocr ocrad (last two are for ocr, so not neccesary, but usefull. At first glance, on some badly scanned text, gocr did the best job. *And* it can do barcodes :-) (automatically)
[*]add this to /etc/udev/rules.d/45-libsane.rules

# Brother DCP-115
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"

(source: [https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/72321](https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/72321))
[*]plug out & in my printer/scanner
[*]it works! (at least, it worked for me)
[/LIST]
Neat to have a company supporting Linux this good. I also have a windows mobile phone, which I don't even dream I can do anything non-bluetooth with it when I don't sit down for 2 days, and this scanner just works (TM) in 15 minutes!

---

### Post by Jose Catre-Vandis on 2007-09-02
Also, check out this great thread about Brother printers/scanners etc

[http://ubuntuforums.org/showthread.php?t=105703&highlight=brother](http://ubuntuforums.org/showthread.php?t=105703&highlight=brother)

---

