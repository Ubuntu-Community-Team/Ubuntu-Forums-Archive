---
title: "Ndiswrapper"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by LarsJohann on 2009-07-19
Could someone here explain to me how to install Ndiswrapper? I'm trying to get my WuA-2340 Wireless Adapter configured with Ubuntu using this guide:

[http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html)

---

### Post by wabbalee on 2009-07-19
[this]("http://ubuntuforums.org/showthread.php?p=7301515#post7301515") is not how to install ndiswrapper but possibly a way to get your wireless to work.

---

### Post by wabbalee on 2009-07-19
have you installed ndisgtk, ndiswrapper-common, ndiswrapper, wicd? the latter will remove package 'network manager'
ndisgtk is a front end for ndiswrapper and appears in the system menu as 'wireless windows drivers'. use that to install your winxp drivers (look for the 'bcmwl5.inf' file on your windos machine) and see if it then says: driver installed and hardware present'. then in wicd select under 'preferences-> general settings-> WPA supplicant driver-> ndiswrapper-> ok'. select your wireless network, click on the little triangle next to the name of the by you preferred network and check the 'automatically connect to this network' box.

that works for me anyway.

---

