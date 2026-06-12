---
title: "Install Samsung SCX-3400 Mutlifunction Printer / Scanner under 11.10"
date: 2012-04-04
forum: Hardware
---

### Post by leogaggl on 2012-04-04
Just in case it helps anybody (I could not find any info for this specific model) I have documented the installation procedures for the Samsung SCX-3400 Mutlifunction Printer / Scanner under 11.10

[http://www.gaggl.com/2012/04/installing-samsung-multifunction-printer-ubuntu-11-10/]("http://www.gaggl.com/2012/04/installing-samsung-multifunction-printer-ubuntu-11-10/")

Both scanner (xsane) and laser printer work nicely.

HTH

---

### Post by for_serg on 2012-05-11
Thanks, and what about using the same series over WiFi (like SCX-3405W)?

I set up the WiFi printer through IPP (although it tends do disconnect when going into sleep mode), but scanning still does not work

---

### Post by FirstByté on 2012-07-09
+1

This confirms that the steps enumerated above works!

Many thanks

:popcorn:

:-({|=

---

### Post by OudeRot on 2012-07-11
SCX-3405W with 12.04 generated at crash error report with colord being the culprit ... wifi not tested yet.

Solved by changing:

ATTRS{idVendor}=="04e8"
to
ATTRS{idVendor}=="04e8", ATTRS{idProduct}="344f", ENV{libsane_matched}="yes", MODE="0666"

in '/etc/udev/rules.d/99_smfpautoconf_samsung.rules'

---

### Post by babistuta on 2013-05-19
I did something else, quick and easy.

I opened the terminal and typed: **sane-find-scanner**
Then I got the scanner type and the usb line like this:
[I]found USB scanner (vendor=0x067b, product=0x2303) at libusb:003:002
found USB scanner (vendor=0x04e8, product=0x344f [SCX-3400 Series]) at libusb:002:006

[/I]After that I typed **scanimage -L** in the terminal, and the scanner was reported as not detected.

Then I went to **/etc/sane.d/xerox_mfp.conf** and to **/etc/sane.d/xerox_mfp-smfp.conf **and I added the following to both files, using the information I got from sane-find-scanner:
[I]# Samsung SCX-3400
usb 0x04e8 0x344f[/I]

Right after and without rebooting, my Mint 13 was able to detect the Scanner of Samsung SCX3400 device.

Hope that helps somebody. It's a really pain this issue.

---

