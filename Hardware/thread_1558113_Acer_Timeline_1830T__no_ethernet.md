---
title: "Acer Timeline 1830T : no ethernet"
date: 2010-08-21
forum: Hardware
---

### Post by gouje33 on 2010-08-21
Hi everybody

I've installed Ubuntu netbook Edition 10.04 on my Acer 1830T

As it's mentionned [here]("https://help.ubuntu.com/community/Aspire1830T#Installation%20Notes") the ethernet card is an Atheros AR8151. I've installed all necessary packages :

linux-headers-2.6.32-24_2.6.32-24.41_all.deb
linux-headers-2.6.32-24-generic_2.6.32-24.41_i386.deb
linux-headers-lbm-2.6.32-24-generic_2.6.32-24.17_i386.deb
linux-backports-modules-headers-lucid-generic_2.6.32.24.25_i386.deb

But the ethernet card is still unrecognized. Network Manager doesn't show neither the ethernet card nor the wifi card.

The wifi chipset needs internet to active the driver...

So what do you think I could do to have internet on my netbook ?

Best regards,

---

### Post by tpdi on 2010-08-31
Assuming you have the same hardware I do -- but and don't assume it, check it with 
sudo lshw -C network.

If that shows a Broadcom card for wireless, follow my instructions here: [http://forum.notebookreview.com/6642885-post1573.html](http://forum.notebookreview.com/6642885-post1573.html)

Basically, you install the Broadcom driver from the install .iso.

For the ethernet (wired), I have an Atheros card. You need to download the source from Atheros, compile it, and install it. I've done this, it shows up in lshw, but I haven't physically tested it.

If you have an ALPS touchpad, that'll have problems too; check out my post on that in these fora.

---

### Post by schmickey on 2010-09-07
This worked for me:
[Atheros AR8151 Fix]("http://ubuntuforums.org/showthread.php?t=1476231")

Follow chili555's directions.

---

