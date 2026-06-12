---
title: "Ubuntu with Intel GMA 3150"
date: 2010-02-22
forum: Hardware
---

### Post by archieboy on 2010-02-22
I have a Sony Vaio VPC-W21M1E, 10" netbook, to which I succeeded to install Ubuntu 9.10 Netbook Remix thanks to the Universal USB Installer from pendrivelinux.com.

The bigger problem starts now. Although the automatic display settings seem ok (1366x768px, 60Hz), there is a terrible flicker problem. It already gave me a headache.

Can this be because of the display driver? How can I reload it?
Any ideas?

Thanks,

Archie

---

### Post by lucas.andion on 2010-02-23
Sadly this graphic chipset works but there are missing so many features.

If you can't wait to the drivers to be on ubuntu repos. You can find them on: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) but fot Intel GMA 3150 you'll need kernel 2.6.32 and so many new stuff... (glibc...)

If the problem isn't urgent i'd wait until April for Lucid to come out.

---

### Post by eschur on 2010-03-15
Hi, 

I have an Acer Aspire 532H which has the GMA 3150. I am now updating to Lucid from Karmic. Will there be "poulsbo" type drivers for this card I can use with Lucid? Are they already available in the repos? If so what are they?

Thanks

---

### Post by postadelmaga on 2010-08-15
try that ppa if u have issue with GMA 3150
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

