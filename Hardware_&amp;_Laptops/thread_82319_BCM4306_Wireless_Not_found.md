---
title: "BCM4306 Wireless Not found"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by UzbrojonyBandyta on 2005-10-26
Hello

I have installed Ubuntu 5.10 on my laptop HP Presario M2000.
Everything has been very nicely detected with the exception of my wireless network card :

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I know It is possible to install it througs ndiswrapper, but when I did it the last time on 5.04, I got some problems:
- ndiswrapper during system startup was hanging the system ( only solution was to start it manually through modprobe )
- the applet showing the strength of signal doesnt work here with ndiswrapper ( although signal strength is shown well under windows )

Besides I find using ndiswrapper a little degrading. It is like commiting to mistake. Acknoledging that things run better on windows.
There should be a better way to get this card to work. Linux after all is a "network" system, so why does network . Does anybody know how ?

---

### Post by marien on 2005-10-26
i have the same problem with my dell inspiron5150.

---

### Post by Neutrino on 2005-10-26
try using ndiswrapper. Then you can install the windows driver and it will recognize your card.
I had the same problem with my wireless usb wifi adapter.
go here :
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by essexman on 2005-10-26
[quote=UzbrojonyBandyta]Hello

I have installed Ubuntu 5.10 on my laptop HP Presario M2000.
Everything has been very nicely detected with the exception of my wireless network card :

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I know It is possible to install it througs ndiswrapper, but when I did it the last time on 5.04, I got some problems:
- ndiswrapper during system startup was hanging the system ( only solution was to start it manually through modprobe )
- the applet showing the strength of signal doesnt work here with ndiswrapper ( although signal strength is shown well under windows )

Besides I find using ndiswrapper a little degrading. It is like commiting to mistake. Acknoledging that things run better on windows.
There should be a better way to get this card to work. Linux after all is a "network" system, so why does network . Does anybody know how ?[/quote]

I have to disagree with you on this and I think your post should not be on the Help forums as this is more of an issue than a fix request.

  Ndiswrapper is good open source software.  There is no mistake.  Manufacturers use cheaper and cheaper chipsets, and ndiswrapper is a way of getting closed source windows drivers to work with linux. Sure, there are GPL issues, but it works, it is free, and will always be so.

I voted with my wallet and bought an edimax card with an 'open' RT2500 chipset, which breezy picks up on installation.  I feel that we should support  'Open' hardware as much as possible but this is no a realistic way forward.

Some people argue that  programs such as ndiswrapper are 'giving in' to Microsoft.  I believe that ndiswrapper is helping to fuel the growth in Linux desktops at the moment and I believe there would be far more Linux desktops running today if a similar solution had been found for 'Winmodems' five years ago.

Please use ndiswrapper or a card with an ['open']("http://www.openforeveryone.co.uk") chipset.  I have both and I am 100% ubuntu on my desktop and laptop.  You could be too.

---

