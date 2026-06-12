---
title: "wireless lan"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by funpop on 2008-01-25
hey there,

i will move to a new flat on 1th of february, there i will share one wireless connection with five other people. i have never ever used a wireless connection before and need to get a wireless usb-stick. 2 friends of mine offered me one for free. i did see _a lot_ of threads about problems with wireless connections, so i want a ubuntu-friendly one.

my brother got something from D-Link that worked out of the box, dont know the brands of the other one's. so my questions:

1. which wlan usb sticks are known to work out of the box ?
2. my desktop got some usb 1.1 slots free and one 2.0, is this important for a good connection ?
3. i got a wireless logitech keyboard/mouse combination (ex110), will this mess with the wireless internet frequency ?
4. there is different encryption: wep, wpa wpa2 and whatnot..which should i use ?

thats it for the moment..
have a nice day,

michael



edit: i see there is a wlan section, would be nice if someone could move the post there :)

---

### Post by jeffus_il on 2008-01-25
Here is a page about Linux Hardware support for wireless devices:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

I have a usb wireless thingie  which needs no special attention made by Tp-Link.

But be careful, the manufacturer is less important than the actual chip used.

My chip is made by Realtek and the system automatically loads two modules when I plug it in:
rt2500usb and rt73usb

They work well.


The 1.1 usb may be fast enough for wireless, but is certainly not for an external disk. (you can purchase a pci usb card for a small amount)

I think that the wireless keyboard will not interfere at all.

The encryption depends on your paranoia, wep is not great but is simple and good enough for me, if you live on a farm and have no-one within a couple of hundred metres, you don't need encryption, If you hold the secrets of how to make a fusion bomb, go for wpa.

---

