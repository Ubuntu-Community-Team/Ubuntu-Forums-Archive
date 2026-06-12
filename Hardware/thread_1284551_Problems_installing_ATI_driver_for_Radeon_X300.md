---
title: "Problems installing ATI driver for Radeon X300"
date: 2009-10-06
forum: Hardware
---

### Post by bawig1 on 2009-10-06
Hi,

I have installed 9.04 on one of my laptops that has a ATI Radeon X300;

```
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

```I want to be able to use 3D desktop effects' and they don't work with the current driver that is used, but when I go to System/Administration/Hardware Drivers there are no drivers listed. It just says 'No proprietary drivers are in use on this system'. Is there a way to manually install the drivers I need?

Thankyou,

Brett.

---

### Post by ssri on 2009-10-07
None of the current proprietary drivers support your card, as ATI placed it on legacy support several months ago.  You will have to use the opensource drivers ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)), which will probably lack the 3D acceleration that you seek.  Another way is to downgrade your xserver and install the last supported proprietary driver for your card ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue))

---

### Post by bawig1 on 2009-10-07
thankyou.

---

### Post by ssri on 2009-10-07
> **bawig1 said:**
> thankyou.

np, and good luck!

---

