---
title: "installing Benq S2W 4300U scanner"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by weemikey on 2006-09-24
I would love to be able to install my Benq S2W 4300U scanner.
It does not work on Ubuntu Dapper Drake altho' it did work on earlier release.
I have installed VueScan (trial edition) and it does detect and run the scanner, however it does imprint $$ signs on each scan :-( and I'd prefer to run strictly under Ubuntu.
Ideas?
Mike

---

### Post by zxee on 2006-09-25
I don't know anything about that model but if you go to the sane site [http://www.sane-project.org/cgi-bin/driver.pl?manu=benq&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=benq&model=&bus=any&v=&p=)
you can search for more info on support there.

---

### Post by vivichrist on 2008-02-07
this scanner doesn't work on gutsy or hardy.
may have something to do with there being no "scanner" module and /proc/bus/usb/ usbfs not being mounted at boot. I think you don't need firmware when using libusb...? which is used instead of the scanner module.

---

