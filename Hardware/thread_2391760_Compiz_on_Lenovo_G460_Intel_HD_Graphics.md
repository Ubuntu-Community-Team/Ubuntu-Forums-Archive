---
title: "Compiz on Lenovo G460 Intel HD Graphics"
date: 2018-05-12
forum: Hardware
---

### Post by pinho2 on 2018-05-12
Dear friends;

 I'm new at this forum but i'm using Ubuntu for quite sometime. I have a Lenovo G460 laptop with 16.04 LTS working really great and i want to install Compiz to add some visual effects. My doubt is if anyone here have already tested those visual effects on a machine like mine or even on this ancient graphics card without problems with Unity and compiz working together.

 I apreciate any answers. My laptop has 8GB Ram, an 500GB SSD and a m380 i3 Intel processor.

 Thanks a lot.

---

### Post by deadflowr on 2018-05-13
If Ubuntu then compiz is already installed.
You can add some extras with the compiz-plugins package and then install compizconfig-settings-manager to set it as you want to try.
unity is a compiz plugin ftr.

i would first install ccsm (compizconfig-settings-manager, for short)
```
sudo apt install compizconfig-settings-manager
```
to see what variety of visual effects and controls Ubuntu already hasd to offer.
and then you might add the compiz-plugins package
```
sudo apt install compiz-plugins
```
(compiz-plugins wil bring in cube settings along with several other effects including extra animations.)

Intel HD is not ancient.
So I do not foresee much problems.

---

### Post by pinho2 on 2018-05-13
Thanks Deadflowr. I installed the manager and the plugins. I had some messages about conflicts trying to enable some of the plugins but i manage to activate some effects. I don't want to make my computer a mess since i need this laptop for work and for now, i don't want to re install the system or upgrade to 18.04. So i'll carefully try to activate the effects.

---

