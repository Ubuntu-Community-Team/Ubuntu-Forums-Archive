---
title: "Changed printer, printing works, simple scan says scanner"
date: 2013-03-15
forum: Hardware
---

### Post by timcredible on 2013-03-15
Had an HP 5250, it broke, I bought an HP 6525, removed the 5250, added the 6525, prints fine, but simple scan says no scanner available.  sane-find-scanner finds the printer:
```
found USB scanner (vendor=0x03f0 [HP], product=0xaf11 [Photosmart 6520 series]) at libusb:007:003

```  
Any ideas?  Thanks.

---

### Post by agillator on 2013-03-15
I assume you are using the version of HPLIP that Ubuntu installs. If so, most likely therein lies your problem. My recommendation is to go to the HPLIP site and download HPLIP from there. Then purge the existing HPLIP and install the one you downloaded. That should solve the problem. It always has for me and I have been using HP multifunction printers for some years. I think Ubuntu, for some reason, configures their HPLIP package without scanner support.

---

### Post by timcredible on 2013-03-15
Thanks, that sounds reasonable, i usually buy older hardware, but got a good price on newer printer, and i see that 12.04 is behind on hplip by a major update

---

### Post by agillator on 2013-03-15
If you have any problem, give a yell. Actually I probably wouldn't hear you yell so it will probably be better if you leave a message. I have found HP's HPLIP to be an easy install.

---

