---
title: "I cannot shut down or logout with Toshiba U200-191"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by diegor on 2007-01-03
Hi, 

first of all I introduce myself to the Ubuntu Community, my name is Diego.

I have a Toshiba U200-191 with Intel core 2 duo: [http://es.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=ES&PRODUCT_ID=122320&toshibaShop=false&toshibaShop=false](http://es.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=ES&PRODUCT_ID=122320&toshibaShop=false&toshibaShop=false)

I have installed Ubuntu Edgy 6.10 (64 bits amd distro), almost everything works fine but I cannot logout. When I shut down, restart or just logout appears a black window (with the cusor top-left) and the sounds: bip, bip, bip, bip, ..... The only thing that I can do then is just to shut down it using the shut down-button (does not work ctrl+alt+ back sp, ctrl+c,...).

I have installed all the packages of Alsa and I have also update Ubuntu (except the kernel). I do not update the kernel because after update it Ubuntu becomes very very slow.

I have also tried with Edgy 32 bits but doesn't wok very well, sometimes it can not start Ubuntu. Drapper hardly works.

Do you know what can I do or try?, Do you need further information about the configuration of the laptop?

Thank very much for your help and your time.

---

### Post by cwhitt on 2007-01-11
If you have an Intel chipset with onboard video (or maybe even if you don't) the problem may be related to the X server causing kernel panics when it shuts down.  Try changing the following setting in your BIOS:

Advanved->CPU Configuration -> Execute Disable Function 

This should be set to ENABLED.

More info:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

Cheers

---

### Post by diegor on 2007-01-29
Thank you!!! I did it and now it works. I have reinstall Ubuntu just in case.

I'm sorry but I was very busy and I had no time to try it until last weekend.

Now I have problems with the intel sound card, but I will try in a new post

---

