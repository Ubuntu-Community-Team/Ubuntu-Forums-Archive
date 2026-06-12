---
title: "Wireless stops working after a couple of days"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by namityadav on 2006-07-28
Thanks to the good folks here, I've been able to get my BCM4318 working on a Dell XPS m140 .. and so I've (For the first time) completely removed Windows XP from my laptop.

But now I'm getting a weird problem .. in a couple of days, the wireless just stops connecting. iwlist shows my ssid, but the dhcp request never completes. Then if I change the ssid (on the router and on laptop) to lets say MyWireless2 from MyWireless, then it connects just fine.

Then after two days, it stops again and I have to change the ssids from MyWireless2 to MyWireless to be able to connect again.

Can anybody guess why this could be happening?

---

### Post by kb3hkg on 2006-07-28
What steps did you try other than changing the ssid?

---

### Post by namityadav on 2006-07-28
I first tried to check the var/log/syslog to find out the reason. It just looked like the dhcp request wasn't getting any response. I checked the router logs, and it didn't get any request.

I then disabled and enabled eth1 .. didn't help, then on changing the ssid, everything worked fine.

I think this is pretty much what happened.

---

### Post by zba78 on 2006-08-01
Not sure if this will help you but I have a similar type of thing that happens and I find that switching off the router (pulling the power cable out of the back), waiting for a few seconds and switching it back on again fixes the problem.

---

