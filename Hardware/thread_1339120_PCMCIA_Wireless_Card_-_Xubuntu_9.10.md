---
title: "PCMCIA Wireless Card - Xubuntu 9.10"
date: 2009-11-27
forum: Hardware
---

### Post by C!pheR on 2009-11-27
Hi all,

I'm about to purchase a PCMCIA card for Xubuntu 9.10 Karmic. I was going to get the Netgear WG511 until I read [http://ubuntuforums.org/showthread.php?t=1307315&highlight=WG511&page=1]("http://ubuntuforums.org/showthread.php?t=1307315&highlight=WG511&page=1")

Can anyone suggest a PCMCIA card that runs 802.11g in Xubuntu 9.10 that will work out of the box, or failing that an online resourse that I can research a card on for myself?

Thanks!

---

### Post by C!pheR on 2009-11-28
Bump. This laptop is for a friend who is nervous enough at trying an OS that isn't Windows, I really want to make this an easy experience for him!

---

### Post by snf1694 on 2009-11-28
Being new to xubuntu myself, i will give you a tip.      I am typing this on a dell inspirion 3800 through wireless Internet.   I am using a realtek 8185 chipset.... on xubuntu if you use any type of realtek chipset the defult driver for these is the 8180 card, even if your card is not  an 8180 xubuntu recognizes it as an 8180.... this means that you have to blacklist the 8180 driver and install the appropriate driver using NDISwrapper which is your friend ;).  my advice to you is to go for it.  tweak it and use NDISwrapper and you should be fine.

---

### Post by C!pheR on 2009-12-07
Thanks for the reply.

Eventually I decided just to plump for it and bought a Linksys [WPC300N-UK]("http://www.linksysbycisco.com/UK/en/products/WPC100?lid=LearnMore_WPC100") for £9.95 in Staples. Turns out that this wireless card works straight out of the box in Xubuntu 9.10 with no configuration required.

Is there a list of devices that work in Xubuntu 9.10 that I can add this card to?

---

