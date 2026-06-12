---
title: "Epson v19 scanner recognised but disfunctional in xsane"
date: 2019-10-12
forum: Hardware
---

### Post by murphy23 on 2019-10-12
I recently tried to install an Epson v19 scanner in my Ubuntu 19.04 system. I downloaded and installed the official drivers from epson (imagescan-bundle-ubuntu-19.04-3.59.2.x64.deb). With that:
[LIST]
[*]I can fully use epson's image-scan utility (scan and preview) 
[*]Scanner is recognized in simple-scan but when I request a scan nothing is happening (scanner is not moving) and a blank file is created 
[*]Scanner is recognized in xsane, I am able to scan but I cannot preview (throws me an error: Failed to start scanner: operation was cancelled) 
[/LIST]
I also noticed that if I launch xsane while image-scan is running the first is unable to detect the scanner.
Do you have any ideas what to try in order to make it work, especially with simple-scan? I read everywhere about the epkowa backend but I am unable to locate it, is it depreciated?
Thanks!
```

$ sane-find-scanner

found USB scanner (vendor=0x04b8 [EPSON], product=0x013c) at libusb:003:015
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
```

```

$ sudo sane-find-scanner

found USB scanner (vendor=0x04b8 [EPSON], product=0x013c) at libusb:003:015
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

And while xsane is not running (when it's running no scanner is detected) :
```

$ scanimage -L 

device `imagescan:esci:gt-s650:usb:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0' is a EPSON Epson_Perfection_V19

```

---

### Post by him610 on 2019-10-12
On this Epson web page [https://epson.com/For-Home/Scanners/Photo-Scanners/Epson-Perfection-V19-Scanner/p/B11B231201]("https://epson.com/For-Home/Scanners/Photo-Scanners/Epson-Perfection-V19-Scanner/p/B11B231201"), about midway down, it states > USB powered — no AC adapter required
Is that true? There is no AC power to this scanner? The power supplied through the USB port may be insufficient to power the scanner. 
If it were my issue I would try connecting the scanner through a powered USB hub.

---

### Post by murphy23 on 2019-10-17
Yes that's true. Usb supplies power and also receives data so I cannot use a usbhub. Also keep in mind this scanner is specifically designed to be usb powered so that must not be the case, given also the fact that I can scan with certain programs (see above)

---

