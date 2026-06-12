---
title: "Wireless was fine, but died after visiting Starbucks!"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by rosslaird on 2006-05-31
I'm using ndiswrapper on my Acer Aspire laptop. It's been working fine. But at Starbucks, after I had purchased an hour of online time (and only about half an hour into my time), my wireless connection suddenly stopped working. Then, after I got home, it continued to not work on my home network. What could be going on here?

On my home network, iwconfig shows the eth1 connection, but without an access point associated.
iwlist eth1 scan shows no scan results.

Could it be that my router somehow died while I was at Starbucks, and this is all a sinister coincidence? 

(The wlan light on the router is blinking, and the manual says that it should be solid, but I think what's meant in the manual is that the light should be solid when there is an active connection. All status reports form the router web interface check out fine, and I have rebooted/shutdown/reset the router multiple times.)

Ross

---

### Post by chriscando on 2006-05-31
Sometimes if my wireless goes down I have to manually bring it back up.
sudo ifdown eth1    //brings it down
then
sudo ifup eth1   //bring it back up

then verify with ifconfig to see if you have an ip address on eth1
hope this helps

---

### Post by rosslaird on 2006-05-31
Thanks for the reply. Yup, I tried ifup, but it can't find any "offers" -- so no ip.

R.

---

### Post by chriscando on 2006-06-01
When you goto System > Administration > Networking and choose properties for your wireless device, can you see your router (or any) from the drop down?

---

### Post by rosslaird on 2006-06-01
OK, this is pretty funny: after trying everything, and I mean EVERYTHING in the realm of wireless configuration (and router configuration), I discovered my problem, by accident:

The wireless status light on the front of my laptop is not only a status light. It is also a button, and by gosh it toggles the wireless on and off when you press it. I had turned the damn thing off.

Then, when I went to move the laptop away from the router a bit (because I was testing for interference in my increasingly desparate quest for a solution), I accidentally hit the button again (since it's in the convenient spot which is right where I grab the computer when I move it) -- and bingo, here comes the network.

Wonders never cease.

Thanks for the moral support.

Ross

---

