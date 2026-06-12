---
title: "manual configured wireless now laptop partially locks"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by dogskull on 2007-12-14
I have a Dell Inspiron 3800.  I just installed Xubuntu 7.10 on it.  I am trying to get a USR 5410 wireless PC card to work with it.  It's detected at startup.  I went into the network settings and attempted a manual setup of the card to my network.  Now when the card is in the laptop I cannot start most applications.  Even command line commands don't work.  If I type "iwconfig" on the command line there is no response.  I cannot start the network monitor.  I cannot start the network settings.  I tried to change the iwconfig wlan0 settings, but cannot do so when the card is not in the system.  When I insert the card, the commands do not respond.  Can anyone give me some advice on this?  Is there a way to clear the wlan0 manual configuration so I can start again???

Thanks for any help!  I really want to get this working!

---

### Post by dogskull on 2007-12-14
I found that if I logged in with the card out of my PC card slots then I could edit my /etc/network/interfaces file and remove all the references to wlan0.  Then when I reinserted the card everything was cleared away.  I still haven't got the card working correctly, but at least my system isn't locking when I insert it!

---

