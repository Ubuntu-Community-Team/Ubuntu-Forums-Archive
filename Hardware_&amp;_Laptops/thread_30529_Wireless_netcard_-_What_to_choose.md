---
title: "Wireless netcard - What to choose?"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by kamstrup on 2005-04-29
I have to pick a wireless netcard for my mom-in-law, and would like to pick one that will 100% work on a linux (read: Ubuntu) machine (out of the box at best).

Any experiences/advice?

Cheers!

---

### Post by heimo on 2005-04-29
What type of card, PCI or PCMCIA (PC-CARD)? Laptop?

I had good luck with 3Com [3CRWE154G72]("http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CRWE154G72") - in Debian Sid (which is very close to Ubuntu). However at that time I was unable to setup WPA (if I recall correctly).

Be sure to check this this page:
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by kamstrup on 2005-04-29
The Wiki page seems very useful! What I'm looking for is a pci or usb device, for an ordinary dekstop computer, to connect to a router with WEP encryption. - Ie. ordinary use on a non-laptop. :) 

The WIKI page would benefit greatly by a "WEP Support"-coloumn...

---

### Post by heimo on 2005-04-29
Those D-link DWL-G520 cards (without +) seem promising, but I'm not sure about availability (wasn't on my favourite shop*). I advice against USB cards. I bought one cheap Belkin 802.11b and it ruined couple days of my life. Drivers were available and it seemed possible to do, but it wasn't for me.

Buy something that's tested and proven to work (preferrably on Ubuntu or atleast Debian). Be careful with those model names. Sometimes even same product with differenct version can have different chipset... So it's better to find at least couple people who can recommend (first hand). That'll save a lot of frustration.

Oh! And don't forget to give feedback to community, if you find card that's easy to configure.



EDIT: Found it. Price ~60€ (FI). It looks good, has removable antenna. I'd probably choose this one.
[url="http://www.amazon.com/exec/obidos/tg/detail/-/B00007LTBI/103-3860801-9054215?v=glance"]Amazon link
[/url]

---

### Post by kamstrup on 2005-05-02
I just learned from this thread

[http://www.ubuntuforums.org/showthread.php?p=155379#post155379](http://www.ubuntuforums.org/showthread.php?p=155379#post155379)

that the acx100 driver isn't in the repos or on the install disk... I can't imagine how people can say that it works "out of the box" in the wiki then :-S It look like it is in dire need of an update.

Cheers

---

### Post by Hieronymus on 2005-05-02
I'm using a broadcom 802.11b wlan card, it works great in both 32bit and 64bit Ubuntu using Ndiswrapper and the windows drivers. 

Grx Hieronymus

---

### Post by donely on 2005-05-02
[QUOTE=kamstrup]I have to pick a wireless netcard for my mom-in-law, and would like to pick one that will 100% work on a linux (read: Ubuntu) machine (out of the box at best).

Any experiences/advice?

Cheers![/QUOTE]
 I would recommend one based on the chipset from [www.ralinktech.com](www.ralinktech.com). They actively support linux

---

### Post by kamstrup on 2005-05-02
Wow and their drivers are actually GPL'ed! Does it work with WEP, I couldn't tell from their product pages...

---

### Post by kamstrup on 2005-05-07
Ok. I ended up using a D-Link DWL520 with the Atheros chipset. It works like a charm! No manual tweaking to be done. Just go to System->Admin.->Networking and enable the wireless interface. Even WEP was a breeze :) Yeeeehaw, my mom-in-law is going to be one more happy Ubuntu-user! 

"Ubuntu. Just Works(TM) - when you have the right hardware"

---

### Post by Fab on 2005-05-07
[QUOTE=kamstrup]I just learned from this thread

[http://www.ubuntuforums.org/showthread.php?p=155379#post155379](http://www.ubuntuforums.org/showthread.php?p=155379#post155379)

that the acx100 driver isn't in the repos or on the install disk... I can't imagine how people can say that it works "out of the box" in the wiki then :-S It look like it is in dire need of an update.

Cheers[/QUOTE]
 just a little note about that:
the acx100 chipset is supported by ubuntu out of the box, that is correct
wep works too, but scanning doesnt (for me)
ubuntu was the first one that had this kind of support for my card (i dont even know another one, and i tried debian sarge and sid, mandrake, suse, and some other more rare ones)

btw, i use the .b d-link dwl520+ (note the + ;))
and i would strongly advise against buying dlink products since they dont open source their specifications.. (if i had known that back when i bought the card + AP, i wouldnt have had so much hassle with my first few linux tries too :P)

---

### Post by ed_agamemnon on 2005-05-07
Don't get a Netgear WG511v3 (Made in China); you have to screw around with ndiswrapper and it's a pain...

(although the WG511v1 and v2 (Made in Taiwan) are apparently fine)

---

