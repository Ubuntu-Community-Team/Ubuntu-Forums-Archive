---
title: "PCTV HD Pro Stick in Feisty"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by madcharlie on 2007-05-06
I'm having some trouble getting my PCTV HD Pro Stick working in Feisty. I'm not really even sure how to start. All of the info I can find is for older releases. When I try to follow those, I get an error message (while trying to compile the module) telling me that I have loadable modules turned off in the kernel and that I can't compile the drivers. I've tried using module-assistant and modconf but can't figure out what needs to be done. All of the walkthroughs mention modprobing em28xx, em28xx-audio, and em28xx-dvb, but only em28xx works, the other two aren't found. Any suggestions?

---

### Post by dgencare on 2007-05-07
Ive spend the last 3 days trying to get my PCTV HD Pro Stick working in Feisty without any luck. I don't know if you will have any more luck than I did, but to get past the step your stuck on try using this source to build the kernel modules:

 hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

---

### Post by XioNoX on 2007-05-12
Since this night the driver work well with feisty, see : [http://doc.ubuntu-fr.org/materiel/pctv_usb_stick](http://doc.ubuntu-fr.org/materiel/pctv_usb_stick)
it is in french but you should understand, just copy/past each line who are in gray

---

