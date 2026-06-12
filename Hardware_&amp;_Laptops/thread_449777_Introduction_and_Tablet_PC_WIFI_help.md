---
title: "Introduction and Tablet PC WIFI help"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by SAAB_93 on 2007-05-20
Greetings
I am new to Ubuntu, been a Mac user and enthusiast for many, many years. At the present I have four Macs: a Macbook, two Powerbooks (12" and 15") and iMac G4.

Several years ago I acquired a Fujitsu Stylistic tablet PC, model number ST4120. It came with Microsoft Windows XP Tablet PC Edition 2005, which to be frank ran poorly on this 933 Mhz PIII machine even when maxed out on RAM at 768MB.

Anyways, I installed Ubuntu 7.04 on the Fujitsu tablet and I must admit, I am impressed. From the built-in support for the digitizer pen function, audio, USB and printers, plus the UI looks great, my experience thus far has been extremely positive. Finding software to make Ubuntu run more like a tablet PC OS seems to be no issue as well.

Praise and success aside now, I cannot get the built-in wifi card to function. When I removed the wifi card I discovered that it is an Intersil card, here are the details: [_LINK_]("http://www.digchip.com/datasheets/parts/datasheet/235/ISL3874AIK.php"). I installed the Intersil Prism package from the package manager utility, but I guess the wifi card still is not recognized as I cannot find it in network preferences. How should I proceed next? I thought the Intersil wifi cards worked okay with linux in general?

Any assistance would be greatly appreciated as I am clueless on what to do next in Ubuntu! Thanks.

---

### Post by bcw on 2007-05-25
I don't know about the Intersil adapter, but you might try using the ndiswrapper driver:
[http://ubuntuforums.org/showthread.php?p=2688436#post2688436](http://ubuntuforums.org/showthread.php?p=2688436#post2688436)

My ST5032D has the Atheros, and I'm getting good results.

Cheers,
Bret

---

