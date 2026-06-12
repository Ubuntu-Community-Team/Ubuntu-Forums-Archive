---
title: "HP 5510 scanner problems"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by tobeyjaggle on 2005-06-03
sane-find-scanner lists my scanner, but sane (or scanimage) cant see it.
It worked on another pc with ubuntu, but never on this one (after 2 installs)
I would be grateful for any ideas.

More detailed notes below ...

I run sane-find-scanner and it says -

found USB scanner (vendor=0x03f0, product=0x3a11) at libusb:002:004

if I run at as sudo it even finds the model -

found USB scanner (vendor=0x03f0 [hp], product=0x3a11 [officejet 5500 series]) at libusb:002:004

but if I run scanimage -L (as root or not) it doesn't find anything.

I know the 5510 scanner can work.  It works on my other PC running the same version of Ubuntu.

My current PC is an AMD64, running Ubuntu Hoary i386.

---

### Post by tobeyjaggle on 2005-06-03
Okay, I installed HPLIP, added "hpaio" to "etc/saned.d/dll.conf" and now scanimage -L recognizes the scanner!

Kooka takes a while to start up, lets me select the scanner, and then says I don't have SANE installed!  Any more ideas?

XSane eventually says - Failed to open device hpaio/usb/officejet_5500_series?serial=... Device busy.

---

### Post by tobeyjaggle on 2005-06-03
I've found that scanimage was failing to find "hpoj",
so I added it, but now it says it doesn't find the scanner!

If i add the one I've lost the other, and vice versa.
Am I the only one in the world who has these problems?

BTW, I've got hpij installed as well.

---

### Post by tobeyjaggle on 2005-06-03
I hope I finally figure this out, and this is of help to someone else
(although I am still anxiously hoping someone else will help)

I started the "hpoj: service and ran "sudo ./hpoj setup"
which add the printer.
It now skips past previous problem, but -
it can't find /usr/lib/sane/it can't find libsane-hpaio.so.1 !

---

### Post by tobeyjaggle on 2005-06-03
After playing with combinations of hplip / hpoj etc.
If i debug xsane (export SANE_DEBUG_DLL=128) then it tells me -

sane_open: trying to open `hpaio:/usb/officejet_5500_series?serial=MY4C9G20JY96'
and says the device is busy / or couldn't open as before.

I've also noticed that I can't have hpoj and hplip installed at the same time - the one uninstalls the other.

---

### Post by tobeyjaggle on 2005-06-03
Still haven't fixed it, but the following has given me something to think about -

[http://hpinkjet.sourceforge.net/hplip_readme.html](http://hpinkjet.sourceforge.net/hplip_readme.html)

---

### Post by tobeyjaggle on 2005-06-03
VueScan talks to the HP 5510, just testing it ...

see [http://www.hamrick.com/](http://www.hamrick.com/)

---

