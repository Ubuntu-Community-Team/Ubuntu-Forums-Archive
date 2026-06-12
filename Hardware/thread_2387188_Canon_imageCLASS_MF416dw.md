---
title: "Canon imageCLASS MF416dw"
date: 2018-03-15
forum: Hardware
---

### Post by john163 on 2018-03-15
Ubuntu 16.04.04

I'm not having any luck printing to or scanning from this device.  SANE isn't seeing it, I don't see that port 8162 is open for scanning.  Printer control panel sees it, but asks me to select from a list of drivers, none of which are for this one.  Canon's website has a driver download, but it's installer says it's for Debian or Fedora/CentOS only.

What's up?  Was this a bad purchase? :-(

---

### Post by pdc on 2018-03-16
Hi John; I am sure you have bought a very fine machine; and I am sure we can get the printer working; and then let's look at the scanner afterwards;

_______

Ubuntu uses debian packages ...... so if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100924010.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100924010.html)

and click to download and SAVE what will be  [COLOR="#0000FF"]linux-UFRII-drv-v350-uken.tar.gz[/COLOR]             ... by default it should end up in your [COLOR="#0000FF"]Downloads[/COLOR] folder

open a terminal ............ hold down the control and alt and t buttons all at once ........

copy each command below; line by line; paste into the terminal; (where control and v are paste in most programmes ........ for the terminal it is control and shift and v so practice that a few times!!)

```
cd Downloads
```

```
tar -zxvf  linux-UFRII-drv-v350-uken.tar.gz
```

```
cd  linux-UFRII-drv-v350-uken
```

then we are ready to run the install script so watch the terminal as it may ask you some questions ........

```
sudo ./install.sh
```

so that should 1) install the drivers and 2) register the printer with lpadmin            ......if you have any icons in your PRINTERS folder for the MF416 already; I suggested deleting them .......  **before you paste the commands in** ...... as the existing icon(s) seem not to work??

(Canon have been very good with driver support; you can see this latest version was issued 8th Feb 2018 and was developed for Ubuntu 17.10; which; as an innovative product; no longer worked with various printers and scanners;)

_________
_________

for the scanner, I am going to suggest you join the mailing list for SANE [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

these are the very friendly and helpful folks who oversee SANE ..... your hardware isn't listed on their Canon page; so you can help them; and others with your device; if they can do some ID etc on the 416; please do join them and help the community

---

