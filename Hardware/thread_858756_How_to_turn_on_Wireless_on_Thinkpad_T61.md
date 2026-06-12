---
title: "How to turn on Wireless on Thinkpad T61"
date: 2008-07-13
forum: Hardware
---

### Post by theedudenator on 2008-07-13
I ran the 64bit version of the Live Ubuntu CD.
Everything seemed fine except I cannot turn on the wireless.
It shows that I have the driver.

When I hit function F5 it just turns the bluetooth on and off.
Not the wireless.

Any suggestions?

---

### Post by tesna on 2008-07-13
what card do you have? if intel 4965 it should be automatically enabled in ubuntu 8.04, if atheros, you need to compile and configure the drivers first. 

btw, on default installation of of ubuntu 8.04, if you have intel 4965 card the wireless led won't turned on even the wireless already on. did network manager shows the list of APs in your area? I need to compile the drivers from source and added one line to enable the LED.

---

### Post by theedudenator on 2008-07-13
I have the Atheros card.

I can see not that it is on but the LED light is off.

BUT..  my connection is not very good.
I could not connect when I was upstairs from the router.
I walked down stairs and it was fine.

If I am more then 20 feet away from the router I lose the connection.

This never happened in windows...

---

### Post by jli127 on 2008-10-28
I got same problem on my  ThinkPad T500. 

Wireless controler is AR242x 802.11abg Wireless PCI Express Adapter (rev 01).  I compiled 'madwifi-hal-0.10.5.6-r3861-20080903' driver.
But the wireless is off. 'iwconfig' shows nothing there.

Can you explain a little more how you solve the problem? Thanks.

---

