---
title: "HP Officejet Pro 8500A as a scanner"
date: 2011-07-20
forum: Hardware
---

### Post by genbie on 2011-07-20
Hi,

Has anyone managed to get the above HP All-in-1 scanner to work? I got the printer to work (only through usb connection though not wireless) but I have had no luck whatsoever in getting the scanner to work. And it is not a permission issue since root can not have the scanner to work either. Any advise appreciated. 

```
sane-find-scanner -q
found USB scanner (vendor=0x03f0 [HP], product=0x5312 [Officejet Pro 8500 A910]) at libusb:001:004

```

```
scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

---

### Post by mhedges48 on 2011-08-08
Hello, just got it to work great on Ubuntu 10.4/Lucid, both printing and scanning. I followed these instructions:
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

