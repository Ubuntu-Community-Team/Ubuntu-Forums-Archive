---
title: "ati 2600 pro agp on  gusty 7.10"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by amihov on 2007-11-17
Hi to all. I am new to linux i have been using it for about 6 months . I upgraded my video card to 2600 pro agp from sapphire and i am having problems installing ati drivers. The card is not recognized by the driver. I was using the 8.42.3 driver. After installation i got black screen. And i was not able to run the ubuntu in grafical mode. I used the aticonfig but that didn't help. I am not sure but if that can cause the problems but i have the feeling that ati driver is not supporting the new cards when they are on agp slot. I had similar problems whit the same card under xp but on the end i manage to install the card by using customized driver by on of the manufactures. Any information will be helpful.
Thank you .
Alex

---

### Post by Brautigam on 2007-11-17
that is a very high quality card from what ive read, are you sure it will be compatible/.?

---

### Post by amihov on 2007-11-17
Well the card is compatible with the drivers but it is agp and the drivers is written for pci i am not 100 % sure about this.

---

### Post by dasher79 on 2007-11-26
You'd be happy to know ATI has just released new drivers supporting ubuntu 7.10!!
They are  "ATI Catalyst™ 7.11 Proprietary Linux x86 Display Driver" and you can find them here: [http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml)

Im looking to buy the same card because of the intergrated audio with the HDMI. Please let me know if you get it **fully functional**, including the sound!! 

------------------------------------------------------------
MythBuntu 7.10 Rocks

---

### Post by amihov on 2007-12-08
The agp card has no drivers for linux. Ati driver will not work. I have tried them all. Don't waist money on this card.

---

### Post by ~/Chromekaldra/~ on 2007-12-15
I'm having the same issue, and i've been going through several help threads and such on other various websites and so far i'm a little confused. Through context it became apparent that i might have to have the card plugged in in order to config for it, but i get a black screen like ^ so how can i do that? 

plus, i ddl the .run file for the drivers but i don't know how to run it...enter, ddl click, 'cd desktop, cd (file name) " returned, "no such file or directory" even though it's right there on my desktop...

I think i need a 'how to book'...

Any help would be appreciated.

*edit*

I'm using a PCI slot for it, as intended, same card as ^, ATI radeon 2600 HD PCI

---

### Post by amihov on 2008-01-18
Well for now you can tray using envy. It maite  work for you it didn't work for me but i have agp so i am not sure.

---

### Post by Yellow Pasque on 2008-01-19
I would suggest using the radeonhd open-source drivers.

---

### Post by samase on 2008-01-19
here it says that it should work... but haven't got it working.

[http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)


and here is thing to check when using AGP:
[https://a248.e.akamai.net/f/674/9206...at81-inst.html](https://a248.e.akamai.net/f/674/9206...at81-inst.html)

---

### Post by amihov on 2008-01-21
Even the new driver is nor working. I just traied it. Ati gives no support to their new agp products. Don't waist any money on them. The driver is just not support agp and thats it.It is just so sad .

---

### Post by samase on 2008-01-21
I've come to same conclusion. drivers just dont support agp. it would be nice to know thatare they going to be supported. radeonhd drivers work but at the moment it is not any better than using vesa drivers.

---

### Post by amihov on 2008-01-22
Some news about the 2600 pro agp. Finally i manage to install the latest ati driver using envy and option manual. The card works but it it is slower then the generic Linux driver. The driver is not supporting the card fully you can use it but is so slow that if i new this in advance i would never spend even a 1 $ on this card. Open GL is running in software mode to bad that ATI ( AMD) is misleading the customers.

---

### Post by amihov on 2008-03-15
Ati has released a new driver that works with 2600 pro agp. ati-driver-installer-8-3-x86.x86_64.run.
This is the driver that worked for me. I will recommend to use the latest version of envy to install the driver because in case of an error it is easy to reverse back to the default vesa driver. I did it using option install ati driver manually from the envy menu and then just pick the correct driver.

---

