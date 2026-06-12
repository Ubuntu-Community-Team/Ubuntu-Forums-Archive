---
title: "wireless pcmcia network card not recognized"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by cjm on 2005-04-23
i would love some help with getting my wireless network card up and running with ubuntu 5.04

at this stage, it doesn't seem to be recognzied at all.  can anyone help?

card details:

BUFFALO WLI-CB-AG54
54Mbps 802.11g/b/a

thanks in advance  O:)

---

### Post by mudra on 2005-04-23
A quick google only turned up a LINUXANT driver that appeared to be a patch for a kernel. I am not sure that it is supported out of the box. Does anything happen when you plug the card in lights etc ....

What does IWconfig give you after you have plugged the card in ?

Hope some of this helps.

Mudra.

---

### Post by cjm on 2005-04-23
thanks for the reply mudra

iwconfig gave me:

lo     no wireless extensions
sit0  no wireless extensions

also, after plugging in the card and checking Device Manager, it showed the following:

BCM4309 802.11a/b/g

 Device
 -----------
 Vendor: Broadcom Corporation
 Device: BCM4309 802.11a/b/g
 Status: Status
 Bus type: PCI
 Device: Unknown
 Capabilities: Unknown

oh.. and no lights show when it's plugged in.

---

### Post by spd106 on 2005-04-23
Hi 

You should probably look at the following excellent wiki how-to

[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

As it's based on a broadcom chip, you'll probably need to use ndiswrapper with the windows driver that came with the card.

follow the links on the ndiswrapper site at 
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 
to find more info about which cards work with it.

Hope this helps

---

### Post by cjm on 2005-04-23
thanks for that... i'll follow that through over the next week or so... 

i'd do it straight away, but the only problem is that the process depends on having a network connection setup... and the only connection i have is the wireless card.

cheers

---

### Post by fordfan753 on 2005-04-23
NDIS Wrapper does work...but not well in a lot of cases.
A friend had NDIS Wrapper issues with his card, after a bit of looking around he found that his card was really another card with different sticker and packaging on it. Look around, see if there are any alternative drivers you can find for it. In his case we found 2.6 Kernel drivers for his card. They were part of an open source driver project. Just keep looking, find out as much as you possibly can about your card, and just keep looking. If you really must you can use NDIS Wrapper, but I have never seen it run with any great success

---

### Post by Staesys on 2005-05-02
I'm using a Motorola WN835G (Broadcom 4306) PCMCIA network card on my laptop right now with the NDISWRAPPER and the windows driver installed. I had some issues earlier getting WEP to work, but I traced the problem back to my Linksys WAP11 not talking to the card well. I just replaced it with a BELKIN F5D7230-4 wireless router and it's working like a dream. Of course, YMMV...

I'm running Ubuntu 5.04 right now on my laptop.

-Paul

---

