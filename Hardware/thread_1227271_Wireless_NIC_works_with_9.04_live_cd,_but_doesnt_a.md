---
title: "Wireless NIC works with 9.04 live cd, but doesnt after upgrade from 8.04"
date: 2009-07-30
forum: Hardware
---

### Post by rslrdx on 2009-07-30
Hi and TIA!

I'm a happy ubuntu user with a little problem, just upgraded from 8.04 to 9.04 and can not get the wireless card to work. 

When I try the 9.04 live cd, the wireless network card is detected and works without a hitch, but in the installed 8.04 system it required ndiswrapper, which was working. 

After the upgrade (from the alternate cd), the network would not conect anymore, but detected the networks available.

Guessing I didnt need ndiswrapper anymore, I removed it and also removed Network-Manager, rebooted and reinstalled Network-Manager.

Now the wireless network card doesnt even show up in the network manager, however the wired nic does show up and works.

So I wonder if anyone knows a way to install the network card only from the live cd, or any other suggestions that I might be able to look into.

Laptop Acer Aspire 5720z

Rodrigo.

---

### Post by rslrdx on 2009-07-30
Got if fixed.

The wireless card had to be blacklisted in the 8.04 install in order for ndiswrapper to work. edited the blacklist config files and the card was installed correctly by 9.04

---

