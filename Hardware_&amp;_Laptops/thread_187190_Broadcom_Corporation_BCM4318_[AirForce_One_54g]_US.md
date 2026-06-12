---
title: "Broadcom Corporation BCM4318 [AirForce One 54g] USE NDISWRAPPERS or bcmCutter"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by jrattner on 2006-06-02
Hi I had a previously functioning network card in the last release of ubuntu.  Now it no longer seems to work.  I'm using the following card Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

Considering the card I have should i set up my wireless card using ndiswrapper or should i try to use  bcm43xx-fwcutter?

Is there an advantage to either method? Do they both do the same thing?  So far neither has performed well for me.

Any suggestions and help would be much apprieciated.

---

### Post by massivevoid on 2006-06-02
I have the same card and I use ndiswrapper. See links in my sig.

---

### Post by jrattner on 2006-06-02
Massavoid, how did you complete the first step:

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

?

---

### Post by massivevoid on 2006-06-02
Go into the source folder and type the following:

```
make distclean
```

```
make
```

```
make install
```

---

