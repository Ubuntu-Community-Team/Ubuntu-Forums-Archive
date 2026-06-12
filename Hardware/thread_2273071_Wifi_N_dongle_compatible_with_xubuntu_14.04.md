---
title: "Wifi N dongle compatible with xubuntu 14.04"
date: 2015-04-10
forum: Hardware
---

### Post by ckrles on 2015-04-10
I have googled a lot with no success and found unclear answers. Could you suggest me a wifi N usb dongle or chipset that works out of the box? These are the ones available at my local store.

[http://pccoste.mobi/catalogo/subfamilia.aspx?ch=040200030200041F01051F0001120007080008080303&id=565](http://pccoste.mobi/catalogo/subfamilia.aspx?ch=040200030200041F01051F0001120007080008080303&id=565)

Thank you.

---

### Post by kurt18947 on 2015-04-10
If wikidevi is correct, the first item on your list, TP-Link TL-WN722N should be plug 'n' play.[SIZE=3] [SIZE=2]It uses the Atheros AR9271 chipset, as as the Netgear WNA1100. I have the Netgear and it works fine last time I used it on Ubuntu-gnome 14.04.2. The second choice, TP-Link TL-WN725N may be easy or it may not be. Version 1 appears to use the Realtek 8192cu chipset which works out of the box but not well. There is a [patched driver]("https://github.com/pvaret/rtl8192cu-fixes") on Github that enables 8192cu based devices to work very well in my experience. Version 2 of the TL-WN725N appears to use the Realtek 8188eu chip which I have no experience with.[/SIZE][/SIZE]

---

### Post by jeremy31 on 2015-04-10
I have a TP-Link TL-WN722N and it is plug and play with Ubuntu 14.04 and has an external antenna which should increase the range

---

### Post by QIII on 2015-04-10
May be a little spendy, but have a look at what thinkpenguin.com has.

---

### Post by ckrles on 2015-04-10
Thank you very much. I think I will probably go for the TP-Link TL-WN722N.

---

### Post by kurt18947 on 2015-04-13
> **QIII said:**
> May be a little spendy, but have a look at what thinkpenguin.com has.

Good point about thinkpenguin.

---

### Post by Mike_Walsh on 2015-04-13
I can confirm that the TP-Link WN-725N, ver. 2, with the 8188eu chipset works 'out-of-the-box' with ANY of the 14.04-generation 'buntus. I have it used it on Ubuntu, Xubuntu, Lubuntu AND Kubuntu with great success.

Prior to the 3.13-0.32 kernel revision, it was a little bit 'hit-or-miss', but the problems have been long since resolved. They probably centred around the inclusion, or rather lack of, the 8188eu driver.

Being a 'nano' form factor, it can be left plugged in permanently.....you hardly know it's even there. I can also confirm that it works exceedingly well anywhere up to around 120m from your router. Beyond this, it gets a bit 'patchy'; the signal may or may not 'drop out'.

I would DEFINITELY recommend this adapter, based on personal experience. It has enabled wi-fi connectivity on my very elderly Dell Inspiron laptop, where there was no wireless card fitted.....nor anywhere to accommodate one. Although having  only 2 USB ports, it's enabled internet access, remote file-sharing with my 'big' desktop, and network printing. Can't ask for more than that.

Regards,

Mike. ;)

---

### Post by weatherman2 on 2015-04-13
I have a couple of USB 802.11n dongles that work in Ubuntu, but I rarely use them anymore.  For desktop machines (where I used to use the dongles), I now prefer to use wireless ethernet bridges instead.  I find cheap Linksys/Cisco routers at thrift stores, put Tomato firmware on them, and turn them into wireless ethernet bridges.  Great for putting any random desktop you happen to be working on the internet without fooling with WiFi drivers etc.  Or great for say waking up your media center remotely via Wake On LAN.  Wired ethernet drivers don't always work automatically out of the box in Ubuntu, but they are much more likely to work than wireless drivers in my experience.

The OP may have a laptop, and a wireless ethernet bridge wouldn't be practical for a laptop, of course.   I prefer to upgrade the internal wireless cards in laptops to better cards when possible.  (It isn't always possible but often is easy.)

---

