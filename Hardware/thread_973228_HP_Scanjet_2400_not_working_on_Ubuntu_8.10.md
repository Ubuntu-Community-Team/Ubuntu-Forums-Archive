---
title: "HP Scanjet 2400 not working on Ubuntu 8.10"
date: 2008-11-06
forum: Hardware
---

### Post by jaime256 on 2008-11-06
I just plugged this hp scanner on my laptop to scan a sheet and when I open xsane it tells me no devices are available. Does anyone have any ideas on how to get this working on this new release? Thanks.

---

### Post by mattman on 2008-11-12
I am having the same issue with an HP 5300c scanner on my desktop pc. Worked fine before I installed Intrepid. jaime256, have you found a fix for this?

---

### Post by jaime256 on 2008-11-12
Hey mattman, sorry I still haven't. I have a usb canon that I just plug in at home. I'm not home so I tried using this one which belongs to my brother, but I'm not having any luck. I ended up using an old fax machine he has to make a copy of the document. I don't know if that helps but if you can find a fax or have one, you may be able to use that in a pinch like I did. The good thing is that you don't need a computer with the fax to make a copy so I hope this helps.

On a side note, I also had problems with an HP laserjet 1220 with the older versions, so I'm starting to think the HP hardware doesn't play too nice with ubuntu, at least not completely. So I guess it's pretty much in the air whether HP will work with your stuff or not...not sure it's just a hunch for now.

---

### Post by jaime256 on 2008-12-13
Okay, I finally got home and had to scan something on 8.10. I plugged in my canon and works with no problem. By now there have been a bunch of updates so I can't say if this had anything to do with the scanner working, but I haven't seen any updates for scanners so I really doubt it. I'm guessing it's more an HP hardware problem.

---

### Post by haeret on 2008-12-27
Hello.
There is a sane driver and instructions of install for HP ScanJet 2400 available: [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php)

For this driver to work libsane must be compiled with sanei_usb module, which is not the case with repository version. libsane provided above _is_ with sanei_usb, but it has another problem ([http://ubuntuforums.org/showthread.php?t=684866](http://ubuntuforums.org/showthread.php?t=684866)) because it's old. I got this scanner working on 8.10 after recompiling the newest libsane (sane-backends-1.1.19) with sanei_usb selected (libusb-dev must be installed before compilation). Refer to resource given above for details. (You can save libsane files got in /usr/lib after install for future installations ;>) Don't forget to add "hp2400" line to /etc/sane.d/dll.conf. Good luck! :>

---

