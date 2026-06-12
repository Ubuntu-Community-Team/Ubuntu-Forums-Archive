---
title: "fglrx: No matching Device section for..."
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by BlackHatRob on 2007-08-27
Hello all.

I have installed Ubuntu 7.04 and I am having trouble getting the fglrx drivers to work with my ATI 9200 SE pci card. I have followed many different howtos for this but always end up at the same point. Whenever I try to start the X server, I get the following error:

(WW) fglrx: No matching Device section for instance (BusIS PCI:5:4:1) found
(EE) No devices detected.

Fatal server error:
no screens found

Can anyone shed some light on this issue?

---

### Post by jocko on 2007-08-27
Unfortunately the version of fglrx in feisty is too new to support radeon 9200.
You may be able to get [an older version]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") to work.
Or stay with the xorg driver ("ati" or "radeon"), it should be ok unless you want tvout...

---

### Post by raijinsetsu on 2007-08-27
Or try adding ```
BusID "5:4:1"
``` to your device section

---

### Post by w4ett on 2007-08-27
> Prerequisites

Make sure the following things are true about your video card:

    *

      It is a 'Radeon' card
    *

      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.


This is from:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

