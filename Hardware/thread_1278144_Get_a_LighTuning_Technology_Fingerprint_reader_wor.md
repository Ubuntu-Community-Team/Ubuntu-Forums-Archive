---
title: "Get a LighTuning Technology Fingerprint reader working"
date: 2009-09-29
forum: Hardware
---

### Post by SpyCatch on 2009-09-29
Hey everybody...
Im new here, cause nobody in my german Forum could help me with this Problem...
I bought an Acer Travelmate 8371 and everything worked out of the box. I was hoping that the Fingerprintreader is also working and installed fprint-demo, but i was unlucky... No Devices found :(
lsusb says me that i've got a

Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc.

fprintreader and I hope to find here somebody who can help me to get this very last thing working...

---

### Post by PhobosK on 2010-04-01
Same problem on Aspire 7738g.
Anyone any info?
I found this from the producer of the scanner but no links available:
[http://www.egistec.com/products/bioexcess-linux.aspx](http://www.egistec.com/products/bioexcess-linux.aspx)

---

### Post by frumple on 2010-07-14
Sadly EgisTech, which is the company behind the Lightuning fingerprint scanners, haven't released a Linux driver, even though they have a Linux Biometric Suite ([http://www.egistec.com/en/products/bioexcess-linux.aspx](http://www.egistec.com/en/products/bioexcess-linux.aspx)).

I have the same problem (Acer Aspire 5940g), right now the only options are to help the folks from fprint to develop a driver for this device and/or contact EngisTech enquiring about a driver release, if everybody that uses Linux and have this fingerprint scanner put a little pressure, they might do it.

By the way, does your fingerprint reader stays hot while the notebook is in use?

Regards,
Eduardo

---

### Post by Lazaruss on 2011-07-14
I just got a response from Egistec, apparently their developers are working on supporting linux.

I've tried doing some usb sniffing, but i'm not getting anything from the program i'm using. Are any of you using xp?

---

### Post by freechelmi on 2011-07-15
For info , it's available on one of the certified Ubuntu Laptops : 

[http://www.ubuntu.com/certification/catalog/make/usb:1C7A](http://www.ubuntu.com/certification/catalog/make/usb:1C7A)

---

### Post by freechelmi on 2011-10-18
> **freechelmi said:**
> For info , it's available on one of the certified Ubuntu Laptops : 

[http://www.ubuntu.com/certification/catalog/make/usb:1C7A](http://www.ubuntu.com/certification/catalog/make/usb:1C7A)


Any News ? I don't get how this device can be certified with no public driver...

---

### Post by freechelmi on 2011-10-20
> **freechelmi said:**
> Any News ? I don't get how this device can be certified with no public driver...


Good news , someone Started writing a driver :

[http://lists.freedesktop.org/archives/fprint/2011-October/000065.html](http://lists.freedesktop.org/archives/fprint/2011-October/000065.html)

But a lot of work is still to do.

i didn't get any response from the manufacturer as usual

---

### Post by Foyaxe on 2011-11-25
Hi there,

I am very interested in a working driver for fprint as well.
My device is ID 1c7a:0603 LighTuning Technology Inc. in a Lenovo B570.
Please update here if there is any progres!

Foyaxe

---

### Post by jimmyco2008 on 2012-05-28
Half a year later...

Any progress with this? I almost want to write the driver myself, if only to "sudo" with the swipe of a finger, I hate entering my password when doing anything with Ubuntu as an OS, besides, this could be more secure, since keyloggers wouldn't have a password to log!

EgisTec seems like one of those companies that doesn't care so long as they have your money, so even though they said they're working on drivers, don't count on it. 

...Anyway I *would* work on a driver if I could, I won't pretend it's easy.

---

### Post by MacAodh on 2012-07-03
*Bump*

Any word on this? I've no idea how to write a driver so....

---

### Post by Alakuloinen on 2012-11-05
Anything new here?

---

### Post by MacAodh on 2012-11-05
Not that I heard, I never got mine working...

---

