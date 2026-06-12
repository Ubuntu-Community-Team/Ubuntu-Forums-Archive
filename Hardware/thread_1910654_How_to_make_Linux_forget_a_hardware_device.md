---
title: "How to make Linux forget a hardware device?"
date: 2012-01-17
forum: Hardware
---

### Post by AnotherMuggle on 2012-01-17
Evening all,

I have had trouble with my internal WiFi card for a long time so it has been blacklisted from mobprobe.  For some time I have been using a USB WiFi adapter which works perfecly but has very low signal strength.  I am now using a new USB WiFi adapter which works perfectly and has a strong signal strength.

iwconfig now reports that my WiFi device is wlan2.  Is there a way for me to make Linux forget the other devices, the blacklisted one and the one with the weak signal, so that I am using wlan0 again?

I know its just a name, but I just wondered if it was possible to change?

Cheers,
TJ

---

### Post by ankspo71 on 2012-01-17
Hi,
You can probably reorder the device names so that the best wireless device becomes wlan0. Here is a link that should give you some ideas on how to do this: [http://unix.stackexchange.com/questions/10254/how-to-change-the-order-of-the-network-cards-eth1-eth0-on-linux](http://unix.stackexchange.com/questions/10254/how-to-change-the-order-of-the-network-cards-eth1-eth0-on-linux)
PS: I don't have any wireless cards so I'm unable to check to see if this works.

---

