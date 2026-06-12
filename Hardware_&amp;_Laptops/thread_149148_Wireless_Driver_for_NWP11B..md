---
title: "Wireless Driver for NWP11B."
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by BlaineM on 2006-03-23
Can anyone point me in the direction as to compiling a driver for the Network Everywhere NWP11B?  Thank You in advance.

---

### Post by BlaineM on 2006-03-23
It is an acx100...  I heard through another forum that this card is a pain to configure, and that it might be easier to just buy an Aironet.

---

### Post by BlaineM on 2006-03-24
Any advice in the proper direction would be appreciated.

---

### Post by BlaineM on 2006-03-24
For anyone wondering, or needing direction in this area also, I am now looking to the acx100/acx111 wireless network driver project from sourceforge.net.  [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

---

### Post by BlaineM on 2006-03-28
I now downloaded acx-20060215.tar, which is the latest release of the driver package for that chipset.  Inside there are instructions to compiling the driver for this hardware.

---

### Post by jml on 2006-03-28
If you have not succeded in getting your card working, I can suggest two cards that do work with Ubuntu 5.10.  One is the NetGear WG511T and the other is the Cisco Aironet 350.  The Netgear Card is an 802.11G card, and the Aironet 350 is an 802.11B card.  Bith cards are recognized by Ubuntu.  You simply have to go into network manager to configure and activate it.  Ubuntu supports unencrypted wireless networking and WEP encryption natively.  If you want or need WPA encryption you need to download, install and configure an application called wpa_supplicant.  hope this helps.

Joe

---

### Post by BlaineM on 2006-03-29
I was thinking of just purchasing the new card and save time on having to compile, but one of my friends suggested compiling a driver for the sake of learning what the process is about.  I kinda enjoy doing this sort of thing, to a point though.  By the way, I live in Mason City, not to far away from Albert Lea.

---

### Post by BlaineM on 2006-08-25
just in case anyone looks at this thread for guidance for this card or the ACX100 chipset, there is a working driver that is shipped with the dapper drake 6.06.  thanks whoever spent the time with this driver.

---

### Post by azidrane on 2006-10-07
Thanks chap! All i needed to do was install WiFi Radar (I don't like messing about with the settings manually) :P

Cheers!

---

### Post by BlaineM on 2007-04-14
I use wifi radar, and I like it also.  Very easy to use.

---

### Post by BlaineM on 2007-06-17
a problem though with using the wpa tkip psk.  the process seems really spotty right now.  I hope that someone develops this a bit farther.

I know that the nwp11b does not support anything outside of simple wep, but I have since upgraded to a better internal card, that gets way better coverage, and I dont have to carry around anything extra with me.

---

