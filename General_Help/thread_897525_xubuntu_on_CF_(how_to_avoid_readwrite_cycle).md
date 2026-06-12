---
title: "xubuntu on CF (how to avoid read/write cycle?)"
date: 2008-08-22
forum: General Help
---

### Post by alfonso78 on 2008-08-22
Hi there,

I have the following issue:

I'd like to install an usable O/S on an [alix3c3]("http://www.pcengines.ch/alix3c3.htm")

I don't have the card yet, so I cannot try.

I'm considering two options: 
- [iMedia linux for Alix]("http://www.imedialinux.com/latest_news/new_imedia_linux_6_0_4_has_been_released")
- [xubuntu]("http://www.xubuntu.org/news/hardy/release")

The point is that I would like to add bluetooth support using this dongle: [Trust ultra small]("http://www.trust.com/products/product_detail.aspx?item=15542")

I know from the producer of Alix that customers have managed to make it work, but I don't have more details.

Probably it would be much easier to install BT support in xubuntu (see [here]("https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters")) but I am afraid that xubuntu would wear out the CF too fast (see [here]("http://www.pcengines.ch/cfwear.htm") and [here]("http://www.kvedulv.de/alix-howto.html")) since xubuntu is not optimized for CF.

Is there an easy howto to apply Kvedulv's suggestions to xubuntu (i.e. mount all UFS-filesystems with noatime and to use tmpfs for all temporary files)

Thank you,

alfonso

---

### Post by alfonso78 on 2008-08-22
forgot to subscribe the thread...

---

### Post by LowSky on 2008-08-22
Your best option is to disable swap. That will limit read write cycles but you will loose some speed from having less cache space as that board only has 256RAM. Can I also suggest a operating system like DSL or even Debian with the XFCE GUI

---

### Post by alfonso78 on 2008-08-22
> **LowSky said:**
> Your best option is to disable swap. That will limit read write cycles but you will loose some speed from having less cache space as that board only has 256RAM. Can I also suggest a operating system like DSL or even Debian with the XFCE GUI

Thank you,

I see DSL has some tips on enabling bluetooth ([here]("http://www.damnsmalllinux.org/dsl-n/f/viewtopic/668.html") and [here]("http://damnsmalllinux.org/f/topic-3-26-17050-0.html")) but they seem pretty dated.

Based on the info I found, disabling swap is just one of the many thing you should do to minimize read/write cycles (see [this thread for example]("http://www.damnsmalllinux.org/dsl-n/f/viewpost/700.html"))

But I'd love to find a comprehensive guide...

[This seems like a pretty good tutorial]("http://kristof.vanhertum.be/?p=3"), I'll try it once I get the box.

DSL seems to have a lot of [applications]("http://www.damnsmalllinux.org/applications.html"), so it could a good choice, thanks.

Still, being very lazy, something that would take care of minimizing read/write out of the box would be nice... ;-)

---

### Post by alfonso78 on 2008-08-22
> **LowSky said:**
> Your best option is to disable swap. That will limit read write cycles but you will loose some speed from having less cache space as that board only has 256RAM. Can I also suggest a operating system like DSL or even Debian with the XFCE GUI

It seems there is some problem with DSL-N.
From [http://www.pcengines.ch/pdf/alix1c.pdf:](http://www.pcengines.ch/pdf/alix1c.pdf:)
Damn Small Linux &#8211; Not (DSL-N)
Tested ok booting from CD (version RC4). Installation to CF card was not successful.

Also, the iMedia linux includes native drivers for the Geode LX CPU.

Guess I'll try to install bluetooth support for iMedia. can't be that hard...

---

