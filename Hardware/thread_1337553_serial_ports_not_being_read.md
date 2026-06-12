---
title: "serial ports not being read?"
date: 2009-11-25
forum: Hardware
---

### Post by SeriousName on 2009-11-25
I'm trying to get my Wacom tablet (Intuos2, serial) to work. I plugged it into the serial port provided by my motherboard, but it doesn't seem to be working (doesn't show up in xsetwacom or wacomcpl). Now, I have a PCI card to add serial ports so I installed that and plugged the tablet in there, to the same result. The card does show up in lspci, and Windows finds the tablet without a problem, so I'm fairly sure these serial ports are working.

It could be that there's a problem with the tablet itself, but it has worked on previous versions of Ubuntu (including 9.04) on a different computer. I don't think I have any other serial devices that I can try in order to test. Is there any program like lsusb for serial ports? If not, what else should I try?

---

### Post by Favux on 2009-11-25
Hi SeriousName,

Are you using 64-bit Karmic by chance?  Folks are reporting problems with serial tablets on 64-bit Karmic but say 32-bit works fine.

---

### Post by SeriousName on 2009-11-25
Oh, as a matter of fact I am using 9.10 64-bit. I guess I'll just have to wait for a fix, then.

Thanks.

---

### Post by SeriousName on 2009-11-30
Update: being impatient, I installed Ubuntu 9.10 32-bit, figuring I'd be able to use my tablet that way. No such luck. Neither my on-motherboard nor my PCI card serial ports seem to work in Ubuntu. Windows detects my tablet just fine, so I'm assuming the serial ports themselves are not defective, and that this is an Ubuntu/Linux problem of some sort.

Does anyone have any more ideas here?

---

### Post by SeriousName on 2009-12-02
Bump. I now have my tablet working under Windows, but it's frustrating because I'd rather use it in Ubuntu.

---

