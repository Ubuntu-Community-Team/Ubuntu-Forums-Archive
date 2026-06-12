---
title: "Flyvideo 3000 PAL Version"
date: 2008-07-05
forum: Hardware
---

### Post by dkc10 on 2008-07-05
Hi, i'm trying to install FlyTV Prime 34 FM (FlyVideo 3000 FM) TV&FM Tuner. I loaded *(sudo modprobe) saa7134 card=2* but i need to know what is the id of my tuner *sudo modprobe saa7134 card=2 tuner=??*.
I Have the PAL/Secam version of FlyVideo 3000 FM. I searched the forum but there are threads only for the NTSC version. Also i need to know which Frequency Table to use (I'm in Cyprus)

The program i use is TV Time.

---

### Post by dkc10 on 2008-07-05
:| Help!

---

### Post by nicholas.urfe on 2008-10-03
Hi.

In case someone needs an answer: you need a couple of things... First, the kernel documentation - and see what kind of tuner you have to use. This is the list for a 2.6.26.5 Fedora kernel (you need to use the right kernel-version name):

```

cat /usr/share/doc/kernel-doc-2.6.26/Documentation/video4linux/CARDLIST.tuner |grep Philips|grep PAL

tuner=1 - Philips PAL_I (FI1246 and compatibles)
tuner=3 - Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
tuner=5 - Philips PAL_BG (FI1216 and compatibles)
tuner=23 - Philips PAL_DK (FI1256 and compatibles)
tuner=24 - Philips PAL/SECAM multi (FQ1216ME)
tuner=38 - Philips PAL/SECAM multi (FM1216ME MK3)
tuner=41 - Philips PAL_MK (FI1216 MK)
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
```

Second, go and find the standard for the country you're in. Use something like this: 
[http://www.primetv.com/kitcrew/standards/item67/](http://www.primetv.com/kitcrew/standards/item67/)

Cyprus has SECAM, so you have to use something like
```
modprobe saa7134 card=2 tuner=3
```
or
```
modprobe saa7134 card=2 tuner=24 
```
or
```
modprobe saa7134 card=2 tuner=38
```

Hope it works.

Edit: I would try this command first (without tuner number etc.)
```
modprobe saa7134 i2c_scan=1
```

---

