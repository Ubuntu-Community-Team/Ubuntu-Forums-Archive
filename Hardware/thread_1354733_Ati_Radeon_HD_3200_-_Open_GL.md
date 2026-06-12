---
title: "Ati Radeon HD 3200 - Open GL"
date: 2009-12-14
forum: Hardware
---

### Post by border on 2009-12-14
I have a HP Touchsmart TX2 with an Ati Radeon HD 3200 graphics card. I want to use it to dj with mixxx. Mixxx uses Open GL to display the waveform, and I cannot live without that feature.
Using AMD's fglrx driver results in buggy (audio) program behaviour which makes mixxx not usable. So I tried using the open source Ati driver which does support my card but only in 2D modus (see [this link]("https://help.ubuntu.com/community/RadeonDriver")). So no Open GL (and no compiz, but that's not very important).

Is there any workaround so I can enable Open GL without my video driver supporting it?
I would be asking for another driver but I guess chances are very slim there is any. 
Do I have to wait for my card to be supported more?

thanks for any input on the matter

cheers

---

### Post by lavinog on 2009-12-14
Which fglrx driver did you use?
Which version of ubuntu are you using?

---

### Post by lavinog on 2009-12-14
[http://www.x.org/wiki/radeonhd%3Aexperimental_3D](http://www.x.org/wiki/radeonhd%3Aexperimental_3D)
I would still see if fgrlx 9-12 will work first.

---

### Post by border on 2009-12-14
excuse me for not mentioning
I use ubuntu Karmic, and some ubuntustudio packages (realtime kernel, I should check it also in the standard kernel for completion)
As for the fglrx driver I tried the one in the repositories, which I guess is xorg-driver-fglrx 2:8.660-0ubuntu4 and packages the 8.66 driver

---

### Post by lavinog on 2009-12-14
ok, maybe fglrx doesn't work with rkernel...I don't have any experience with it.

---

### Post by mdshaver on 2010-01-23
The below page discusses how to get the experimental open source mesa drivers working with with Fedora 12. It sounds pretty easy so this may be worth a look if you're having difficulty with Karmic.

[http://gofedora.com/fedora-12-ati-catalyst-drivers/](http://gofedora.com/fedora-12-ati-catalyst-drivers/)

---

