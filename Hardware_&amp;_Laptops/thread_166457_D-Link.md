---
title: "D-Link"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by bushmac on 2006-04-26
Hi, I have just installed Ubuntu on a laptop but the D-LinkDWL-650+ is not reconised, have contacted D-Link they say no drivers.Anyone have some bright ideas?
Cheer
bushmac.

---

### Post by savas on 2006-04-26
Hi. You may use ACX100 driver with this card. But you should notice this;

The + in DWL-120+, DWL-520+ and DWL-650+ is what's important:
The normal version uses the good and well-supported Prism 2.5 chipset, whereas the + version uses the obscure ACX100 chipset.
Oh wait, it's even worse: a newer version of the DWL-650 (the one with grey antenna) is said to also have the ACX100, so it's even more difficult to tell them apart!! ARGH! Consider not buying these cards! (plus, the 650+ seems to be defective/problematic much more often than other cards, in my experience)


[http://acx100.sourceforge.net/matrix.html](http://acx100.sourceforge.net/matrix.html)

---

### Post by az on 2006-04-26
[QUOTE=bushmac]Hi, I have just installed Ubuntu on a laptop but the D-LinkDWL-650+ is not reconised, have contacted D-Link they say no drivers.Anyone have some bright ideas?
Cheer
bushmac.[/QUOTE]
It will work with ndiswrapper.  You may need to prevent a linux driver from trying to use the device.

Please post the output from

dmesg

in a terminal.

---

