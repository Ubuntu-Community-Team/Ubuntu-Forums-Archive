---
title: "Another Wireless Card Question"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ldavey on 2005-10-16
Hi ... 

i am new to linux as of 3 days ago, i installed redhat but then i came accross ubuntu .... and am loving it .... intend on making this my primary OS if i can get a wireless card up and running ...

I have a old DWL 650+ (old one 22mbits) .. after much research i found it uses the TEXAS instruments chipset so basically is made by anti linux driver programmers, and i should try and get a atheros chipset for good compatibilty

Anyway i found some old thread on this site about a year old about wireless cards but didnt really want to post on very old threads so here is the link ... [http://ubuntuforums.org/archive/index.php/t-1881.html](http://ubuntuforums.org/archive/index.php/t-1881.html) and **MDUDZI** said:

[I]"I've had good success with the said chipset as implemented by D-Link as detailed below -the price was acceptable too .
**D-Link DWL-G650 ver.C2** is a very good card to use. I almost got rid of the card after D-Link support would not ackowledge that their WinXP drivers are extremely inefficient but since using the card -autodetected and installed by Ubuntu- on Linux I'm thourougly please and the loading of the CPU is hardly noticeable. WEP isn't good though and I don't know whether its the AP's fault or the card or the software."[/I]

[http://www.dlink.com/products/?model=DWL-G650]("http://www.dlink.com/products/?model=DWL-G650") Might sound very stupid but can anyone tell me if this  is the same card as he did post that a year ago ? and i dont want to go wasting money ! 

Would this card work with linux straight form the box ? because i have tried everything to get my 650+ to work ... incl NDIS, Wireless Tools etc and CBA anymore .. would rather spend a little money for a new card and wont be supporting TEXAS INSTRUMENTS anymore !

Thanks

---

### Post by Anthem on 2005-10-16
I'm curious as well.  A more general question, I guess, is this:

Is there an Ubuntu HCL out there for wireless cards that are known to work out of the box on open/WEP/WPA networks?

While I've gotten my Linksys WPC54GS to play nice with my home network, I've had all kinds of problems trying to get it to roam to different networks.  Feedback is usually along the "blame the drivers" line, which isn't useful if I'm using the best available (but still non-native) drivers.

---

### Post by spd106 on 2005-10-21
> Is there an Ubuntu HCL out there for wireless cards that are known to work out of the box on open/WEP/WPA networks?

I'm currently trying to find an answer to this conundrum.

The [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") contains a list of wireless cards that users have got working. However the biggest problem is that a lot of the cards that do work are old and difficult to obtain easily. Added to this it matters what model version and firmware each card has. The chips on the cards even on the same model can change. Often this information is not explicitly noted on the box.

I suppose if you can track down a linux friendly retailer that will help you out, it might be easier.

---

### Post by bionnaki on 2005-10-21
that's a guide that we could all use - thanks for doing that.

however, the linksys wmp54g card listed on there says it works out the box with the ralink drivers. this wasnt my experience - I had to use ndiswrapper + the rt2500.inf driver from the windows cd to make it work.

---

