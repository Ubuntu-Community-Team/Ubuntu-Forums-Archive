---
title: "new NIC not recognized"
date: 2010-04-22
forum: Hardware
---

### Post by vsiege on 2010-04-22
I installed a new NIC card in my 8.10 box and I'm not able to access the network at all. The old card was operating just fine (part of the motherboard) but this one is faster. Currently the card is showing an LED light on 100 (but it supposed to get 1000) and it doesn't work at all. How do I troubleshoot this? I did not install any software/drivers.

The card I installed was a Netgear GA311. Ubuntu is reading the card as Netgear RTL-8169 Gigabit Ethernet.

---

### Post by P4man on 2010-04-22
I think that card is supported out of the box since ubuntu 9.10. If you dont feel like upgrading, you'll probably need to fetch, compile/install drivers from realtek site. Think these ones:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#5,7,8,10,982](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#5,7,8,10,982)

in a week or so, 10.04 LTS is released though, maybe thats a good time to upgrade?

---

### Post by vsiege on 2010-04-22
thanks. I'll take a look there and try to install the driver. I think waiting to upgrade to 10 would be better too.
I take it I can use the win xp drivers from here instead of the ones that came with the device when I want to install it on that side too

---

