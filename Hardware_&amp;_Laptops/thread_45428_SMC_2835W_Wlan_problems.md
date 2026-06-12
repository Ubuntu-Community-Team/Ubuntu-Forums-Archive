---
title: "SMC 2835W Wlan problems"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Benjamin_Lebsanft on 2005-06-30
dmesg tells me:

[4294714.155000] eth1: resetting device...
[4294714.155000] eth1: uploading firmware...
[4294714.464000] eth1: firmware version: 1.0.4.3
[4294714.464000] eth1: firmware upload complete
[4294715.464000] eth1: no 'reset complete' IRQ seen - retrying
[4294716.464000] eth1: no 'reset complete' IRQ seen - retrying
[4294716.464000] eth1: interface reset failure
[4294716.464000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[4294716.514000] eth1: resetting device...
[4294716.514000] eth1: uploading firmware...
[4294716.633000] eth1: firmware version: 1.0.4.3
[4294716.634000] eth1: firmware upload complete
[4294717.634000] eth1: no 'reset complete' IRQ seen - retrying
[4294718.634000] eth1: no 'reset complete' IRQ seen - retrying
[4294718.634000] eth1: interface reset failure
[4294718.634000] prism54: Your card/socket may be faulty, or IRQ line too busy :(

how do I fix this or is this not a problem. Additionally I can't find any networks, no accesspoints etc.

---

### Post by nocturn on 2005-07-01
[QUOTE=Benjamin_Lebsanft]dmesg tells me:

[4294714.155000] eth1: resetting device...
[4294714.155000] eth1: uploading firmware...
[4294714.464000] eth1: firmware version: 1.0.4.3
[4294714.464000] eth1: firmware upload complete
[4294715.464000] eth1: no 'reset complete' IRQ seen - retrying
[4294716.464000] eth1: no 'reset complete' IRQ seen - retrying
[4294716.464000] eth1: interface reset failure
[4294716.464000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[4294716.514000] eth1: resetting device...
[4294716.514000] eth1: uploading firmware...
[4294716.633000] eth1: firmware version: 1.0.4.3
[4294716.634000] eth1: firmware upload complete
[4294717.634000] eth1: no 'reset complete' IRQ seen - retrying
[4294718.634000] eth1: no 'reset complete' IRQ seen - retrying
[4294718.634000] eth1: interface reset failure
[4294718.634000] prism54: Your card/socket may be faulty, or IRQ line too busy :(

how do I fix this or is this not a problem. Additionally I can't find any networks, no accesspoints etc.[/QUOTE]

I don't have this problem with my card.  
Maybe there is something wrong with the card or the PCMCIA slot of your laptop is not functioning properly.  What kind of laptop is it in?

I'm running Hoary with the default kernel (i686 architecture).

---

### Post by nocturn on 2005-07-01
I found this reference on the net:

> 
The State of 802.11g Wireless Networking in Linux ([http://news.tiker.net/node/205](http://news.tiker.net/node/205))

The Intersil PrismGT was a hopeful contender, until the card manufacturers discovered that they can save a few cents on each card if they stick the MAC-layer processing into the host driver instead of the card’s firmware. (This cheaper type of card is called SoftMAC and will make the prism54 driver complain about “no 'reset complete' IRQ seen - retrying” and “prism54: Your card/socket may be faulty, or IRQ line too busy”). The driver is complete, functional and open, but it doesn’t support the SoftMAC cards, and the earlier hardware versions that aren’t SoftMAC are nowhere to be found, not even on ebay.


So, maybe you have a different 2835 then I do.

---

### Post by nocturn on 2005-07-01
The recommended workarround for most people seems Ndiswrapper.  I don't know if the prism54 driver will support softmac in the future...

---

### Post by Benjamin_Lebsanft on 2005-07-01
bastards ](*,)

I'll try to find another card and send this one back. Any recommendations except SMC cards ^^ ?

---

