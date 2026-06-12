---
title: "Slide scanner film converter"
date: 2009-11-05
forum: Hardware
---

### Post by Smbrandes on 2009-11-05
Hi,

   Ubuntu has been good, but I have run into a puzzle. I have this device called a film slide scanner converter made by Innovative technologies that is a USB device that is supposed to scan old slides and make them into image files. Does anyone know if it is possible to get the thing to work natively. I tried Wine and that did not go well either. 

S.B.

---

### Post by desertdog on 2009-11-05
The place to ask is on [www.sane-project.org](www.sane-project.org). I did a quick search of sane's support devices and the mailing list archives, and Innovative does not show support. 

There is a chance that this is a clone of another scanner that is supported. 

If you plug it into your linux machine and at the terminal type $lsusb you should be able to get the usb vendor id and product id. You can also type $sane-find-scanner -v -v and get the same information plus it might be able to detect what chip is in the scanner. 

You can either post the results here or send them to the sane project mailing list.

---

