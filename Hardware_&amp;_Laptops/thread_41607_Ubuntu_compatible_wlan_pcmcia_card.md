---
title: "Ubuntu compatible wlan pcmcia card ?"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by Benjamin_Lebsanft on 2005-06-14
Just bought an used laptop and now I'm trying to find a linux compatible wlan pcmcia card. Which brand would you recommend ?

---

### Post by nocturn on 2005-06-14
[QUOTE=Benjamin_Lebsanft]Just bought an used laptop and now I'm trying to find a linux compatible wlan pcmcia card. Which brand would you recommend ?[/QUOTE]

I have an SMC 2835 (54MBps).  It is fully supported by the kernel (autodetected).

---

### Post by jakev383 on 2005-06-14
I'm using an Orinoco B/G card, and everything seems to work well. I have yet to find a nice "profile manager" for the 7 different WAPs I use, but who's complaining? Nothing a little scripting can't fix!

I tried 2 Linksys WUSB11 adapters, but didn't have the drivers to use ndiswrapper, so can only say out of the box they didn't work. (I was going to shoe-horn one of those into the floppy bay of my old laptop to get "integrated wireless" <grin>)

---

### Post by Benjamin_Lebsanft on 2005-06-14
[QUOTE=nocturn]I have an SMC 2835 (54MBps).  It is fully supported by the kernel (autodetected).[/QUOTE]
this one ?
[http://geizhals.at/deutschland/a53374.html](http://geizhals.at/deutschland/a53374.html)

---

### Post by nocturn on 2005-06-14
[QUOTE=Benjamin_Lebsanft]this one ?
[http://geizhals.at/deutschland/a53374.html](http://geizhals.at/deutschland/a53374.html)[/QUOTE]

That's the one.  It uses the prism chipset (it says prism nitro on the box of the card).
I even did the update step of my initial install over it.

---

### Post by ecliptik on 2005-06-14
The Netgear WG511v1 (you can get them at Fry's) card works flawlessly with Hoary, just had to add my network info in /etc/network/interfaces and I was set.

[http://kbserver.netgear.com/products/wg511v1.asp](http://kbserver.netgear.com/products/wg511v1.asp) - v1 may not be available anymore

[http://www.netgear.com/products/details/WG511.php](http://www.netgear.com/products/details/WG511.php) - v2, not sure if it works or not

Looking at the prism54.org list of supported cards both appear to be fully supported:

[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

---

