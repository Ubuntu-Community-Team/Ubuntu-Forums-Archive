---
title: "[really LOL-BUG] wifi chipset ipw3945"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by iDleR on 2007-08-11
I've just got a Lenovo Ibm Thinkpad R60 with an Intel PRO/Wireless 3945ABG. 
I've installed on it Ubuntu 7.04.
Ubuntu had no problem installing this wifi card but it works in a really freaky way: if the laptop is on battery mode and it is not really close to the router, the network manager finds the network but it ask always for wep key in loop. I insert the correct key but it ask me the key again. Obviously it is not able to connect.
If the laptop is in charge mode everything works fine.

Anyone knows something about it? :lolflag:

---

### Post by EXCiD3 on 2007-08-11
wow, that is possibly the wierdest bug i have ever heard of. :) i have the same wireless, but have never had a problem like that. You might try reinstalling Ubuntu and seeing if it does the same thing again.

---

### Post by iDleR on 2007-08-11
I've found this: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110)

> 

I have the same problem, but i can relate it with conditions:
the trouble appears often when i am in battery and rarely when i'm plugged to the line power.

The trouble appears when there is lot of wifi traffic, differents networks.

I hope intel move about.

Regards

Stefano


edit: I used the cd sent me by Canonical, I will try with a downloaded iso.

---

### Post by iDleR on 2007-08-12
Ok, I've found a solution...but I really don't know why it is working only using the following way :D

I'm a Debian and Gentoo user so I don't really appreciate gui interface. 

So I edited the /etc/network/interfaces inserting this code:
```

wireless-rate auto
wireless-essid "essidname"
wireless-key xxxxxxxxx enc open
wireless-channel 6
wireless-mode managed
iface eth1 inet dhcp

```

but I had the same problem showed up there.
Then I used my secret weapon: the .won.sh :P

```

#!/usr/bin/sh
iwconfig eth1 rate auto
sleep 2
iwconfig eth1 mode managed
sleep 2
iwconfig eth1 channel 6
sleep 2
iwconfig eth1 essid dierrelabs
sleep 2
iwconfig eth1 key abcdef0123 enc open
sleep 2
ifconfig eth1 up
sleep 2
dhclient eth1
```

and now my wireless is working everywhere in AC power and in battery mode.

I hope it could be useful for somebody else.

---

