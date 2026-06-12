---
title: "HP G2410 Scanjet not working"
date: 2010-09-07
forum: Hardware
---

### Post by Beanmonster on 2010-09-07
Hey guys, once again after days of searching the net for a solution, I turn to the helpful folk here for advice...

On all my other installations of Ubuntu 10.04, I plug my HP G2410 scanner in, and it works with Xsane and Simple-Scan flawlessly!!! :p

However, I recently redid my desktop with 10.04.1 and the scanner just refused to be recognised :( 

I already had HPLIP setup and installed but they do not support the device and refer you to sane drivers.

I continued to install the one found [here]("http://lists.alioth.debian.org/pipermail/sane-devel/2009-January/023517.html") for HP G2400.

Simple-scan recognises a scanner but cannot connect to the scanner when attempting to scan then proceeds to quit when trying again and xsane produces the error:

"*Failed to open device 'hp2400:libusb:002:008': Access to resource has been denied*."

scanimage -L shows (with no errors):
```
device `hp2400:libusb:002:008' is a Hewlett-Packard hp2400 flatbed scanner
```

**_<<<HOWEVER>>>_**
Running xsane as ROOT gives me two scanner options:
[LIST]
[*]hp2400:libusb:002:008 - [SIZE="3"][COLOR="SeaGreen"]WORKS[/COLOR][/SIZE]
[*]genesys:libusb:002:008 - [SIZE="2"][COLOR="Red"]Invalid argument[/COLOR] when attempting scan[/SIZE]
[/LIST]

Running simple-scan as ROOT also gives me two scanners, the one that is presented when running as normal user produces the same error, yet the new scanner option scans but terribly out of dimension and skewed.

How can I fix this? I just want one scanner that I can plug in and scan, no issues...

any help is, as always, tremendously appreciated.;)

---

### Post by phsilver on 2010-10-12
this is the error when I try to execute as a Root:

xsane: symbol lookup error: /usr/lib/sane/libsane-hp2400.so.1: undefined symbol: sanei_usb_init

Never works!!!

---

