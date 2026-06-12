---
title: "ACER ENE card reader and LUCID Lynx(10.04)"
date: 2010-10-06
forum: Hardware
---

### Post by rvndrk3233 on 2010-10-06
any updates on a quasy-working driver..hearing some rumors of <2GB working and others saying there is no driver. There is a driver from Win XP-7, and the HW works in windows.Vendor specific or not, this shouldnt be too hard to wrap a driver layer with.

We have wine , after all.

I have a Gateway LT21 (mislabel as Acer).Everything but this works, and the ATT 3G card works out of the box(with some minor config after install).Not so with Verizon, nTelos, and Kricket, which require the USB dongle flopper.

---

### Post by avacado on 2010-10-14
If you are reading this, chances are you have the same card reader.
try open a terminal and type  lsusb and hit enter if you have device Oc2f:6250 then you have the samedevice as me.
other distributions have the same problem - no driver.

subscribe to my bug 
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/633852]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852")
this adds weight to the issue

It may take some time for s volunteer developer to write a driver.
In the mean time I suggest you buy a card reader or use your camera as an external drive with the card.

update the linux compatibility netbook page to add your model and problem

---

### Post by rvndrk3233 on 2010-11-03
aparently, this worls on linux 4 one with a patched driver set, and there are some other optimizations.

perhaps we can include such patches into the kernel/ubuntu tree and NOT EFF them up, as some drivers have been EFFED up?

I have to look at the project and test and see. Its based off of ubuntu 8.04. Sources should be somewhere or the patch easier to figure out. Will keep posted.
In meanwhile, some users report loading mmc_core, shhci, and mmc_block in /etc/modules seem to work. 

I get the same response as before.



I have the 04u model, AKA Acer One 532H.

---

### Post by yahmorah25 on 2010-11-07
hey i have a acer aspire one 532h and the only thing i dont have working on it is the card reader can any one help

---

