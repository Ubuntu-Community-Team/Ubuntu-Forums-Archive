---
title: "Epson CX9400F scanner config in Karmick Koala"
date: 2009-11-15
forum: Hardware
---

### Post by harrystrent on 2009-11-15
Anybody been able to get the scanner working?

---

### Post by Axx83 on 2009-11-15
applications>accessories>terminal
```
sane-find-scanner
```
write down the usb adress of your scanner
```
sudo gedit /etc/sane.d/epson2.conf
```
there's an example, write your adress under that example, close and save and run xsane.

---

### Post by Holonet on 2010-02-27
I'm having the same problem.  I installed the libsane-extras package, nothing...  I then tried the method just mentioned.  sane-find-scanner did find a USB scanner, as it should have.  I edited the address and saved, but for some reason it didn't change a thing.  I tried scanimage -L and just running xsane, but it detects nothing.

I've read in previous versions people got this to work by installing libsane-extras alone...which should be included with selecting the printer driver if necessary.  Seems this is just getting worse...=D>

---

### Post by ellgor on 2010-02-27
Hi,

Go to the "Avasys" site, its for Epson's, and get their Imagescan package, look for the deb package as its the easiest to install, works after a reboot.

Regards, Ellgor.

---

### Post by stochasticjack on 2010-02-27
Yeah, that Imagescan doesn't work for me.  9.10 with an NX415.  It just says "Could not send command to scanner."

---

