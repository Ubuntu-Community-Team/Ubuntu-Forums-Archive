---
title: "Gateway ML6720 wifi problems"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by eatwhatcom on 2008-04-07
Good day,
I just purchased a gateway ML6720. Thus far it is a really nice machine for the price, but it has Window$ on it. I installed Ubuntu 7.10 and fixed the screen display issue. I'm now trying to fix the wifi. I followed this post to do that:
[http://ubuntuforums.org/showthread.php?p=3994989](http://ubuntuforums.org/showthread.php?p=3994989)

I followed the suggested instructions After sudo modprobe ndiswrapper, networkmanager finds my networks. I click on my network and try to login. Networkmanager connects to my router, an ip address is acquired, 100% signal strength.  All seems to be good with the world at this point. Seconds latter, signal strength goes to 0%. A few seconds after that, networkmanager disconnects the connection, searches for networks, re-connects to my network, 100% signal, then 0% signal...... on and on.  Loops like this for ever.

When I boot up, I have to sudo modprobe ndiswrapper. 

Any ideas here would be great. Thank you for your time

---

### Post by fasteryet on 2008-04-16
The connection dropping over and over again sounds like the problem I had. I got it to work by disabling roaming mode. Go to System>Administration>Network>Wireless connection>Properties then uncheck Enable roaming mode then enter your settings.

---

