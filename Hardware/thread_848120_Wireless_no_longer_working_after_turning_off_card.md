---
title: "Wireless no longer working after turning off card"
date: 2008-07-03
forum: Hardware
---

### Post by coblenis on 2008-07-03
Hello, 

I have an HP dv6608ca laptop with a Broadcomm 4311 (rev02) wireless card.  I recently installed Ubuntu Hardy and used the following guide to get my wireless card working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

There's an external switch on my laptop that powers down the wireless card (the light turns to orange from blue when I do this).  I can't see wireless networks after switching the card on (the light turns blue).  

When I click on the network manager I see "Connect to a 802.1X protected wired network" but nothing for wireless.  

I went through the above guide to see if it would reactive my card, no luck.  

Any thoughts on what to do?

---

### Post by sergiom99 on 2008-07-03
I have the same issue and I go around with
```
sudo /etc/init.d/networking restart 
```

I am not in my laptop now, so the path might not be entirely right, but you'll get the idea.

---

### Post by coblenis on 2008-07-04
After running that command line and a reboot, my wireless is up and running, thanks!

---

### Post by sergiom99 on 2008-07-04
yes, but I think you should do it everytime you move the switch and then you got no wifi.
This command just restart your network.

---

