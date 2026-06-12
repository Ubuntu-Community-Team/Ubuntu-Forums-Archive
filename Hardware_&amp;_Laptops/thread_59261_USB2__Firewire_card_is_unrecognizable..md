---
title: "USB2 / Firewire card is unrecognizable."
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by vrl2 on 2005-08-23
Hello,

I am having trouble getting Linux to recognize the following card:
Syba SD-PCB-COM USB2 / Firewire card
Chipset: M5271
Product Info: [http://www.syba.com/product/43/05/01/](http://www.syba.com/product/43/05/01/)
It offers 2 USB2 ports and 2 firewire ports.

When I insert it and run 'cardctl ident 0' [when this card is plugged into slot 0] I am given the message "no product info available."  The system has no trouble, however, recognizing my wireless PCMCIA card [linksys wpc11].

Strangely, though cardctl cannot see this device, linux does register it in the following way: in KInfoCenter, under "USB DEVICES" the proper number of USB ports are displayed after I insert the SD-PCB-COM

What could be the trouble?  The card not only refuses to be recognized, but when I insert it it actually changes the existing configuration with the other PCMCIA devices.  After I insert the SD-PCB-COM, the usually-working linksys card [though it can still be recognized with cardctl] is permanently set as "disabled"  in the network setup [in the control center].  There are windows and mac drivers available for this troublesome SD-PCB-COM, but unfortunately I'm unsure about how to make it work under Linux.  Is it possible to use the windows drivers to
construct a driver for linux?


I'm running the latest version of Ubuntu.  My computer is a IBM Thinkpad A21m. If anyone can think of any possible solutions, I'd love to hear them.  Please let me know if I can clarify anything about this problem. Thanks!

Venkat

PS - This is my first post, and I am also completely new to Linux. Please let me know if I've posted anything incorrectly or if I am overlooking something obvious.

---

### Post by s_p_a_r_k_y on 2005-08-23
Welcome to the wonderful world of linux ; )
when you plug the card in what does running 
```

dmesg | tail

```
from a console show you?

---

