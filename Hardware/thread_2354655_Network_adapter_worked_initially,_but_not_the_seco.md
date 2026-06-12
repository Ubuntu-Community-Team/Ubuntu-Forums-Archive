---
title: "Network adapter worked initially, but not the second time"
date: 2017-03-04
forum: Hardware
---

### Post by elias.bothell on 2017-03-04
[COLOR=#111111][FONT=Ubuntu](I am running Ubuntu Core QT-Embedded on a nanoPi Neo using this network adapter: [https://www.amazon.com/gp/product/B00MXD2T5G/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B00MXD2T5G/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1))[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The first time I used the network adapter it worked perfectly. I saw the adapter when I typed ifconfig -a and it connected to my network when I typed the following commands:
[/FONT][/COLOR]
ifdown wlan0 
ifup wlan0

[COLOR=#111111][FONT=Ubuntu]But now it doesn't work.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tested it out on my Windows machine and the adapter works fine, and when I type lsusb I can see a network adapter so I'm very confused.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How can I resolve this issue?[/FONT][/COLOR]

---

### Post by betchern0t on 2017-03-06
Couple of things you can do to begin trouble shooting:

1) see what the USB bus says - at the commandline "lsusb" and see if you can spot it.

2) unplug it and plug it back in. Then at the command line type: "dmesg" At the bottom you should see Linux loading the drivers for this dongle.

3) At the commandline type in "iwconfig" (you may have to install it). That will check all interface adapters and list any with wireless capability. You should see this dongle listed with wireless extensions.

4) at the commandline type in "iwlist scan" and if the dongle is working at a hardware level it should list all the wireless networks it can see.

If  you can get through all that, then the issue is actual wireless setup.

Cheers Paul

---

