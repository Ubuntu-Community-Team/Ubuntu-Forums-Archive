---
title: "Airodump-ng does not capture wpa handshake"
date: 2009-07-26
forum: Hardware
---

### Post by Divider on 2009-07-26
```
sudo airodump-ng --bssid 00:00:00:00:00 -c 0 -w mydump mon0
```

Faq:
Aircrack Version? = 1.0rc3

Is your chipset supported? = YES

Packet Injection = YES

Is it in monitor mode? = YES

Your mac and channel are wrong = No this is an example

Is your router in tkip or aes? = TKIP

Are you close enough = Its my router I'm about 14 inches from it.

Are you using another computer as well to attempt handshake = yes

Hardware? = Asus EEEPC900a , Jaunty, Atom Proc., Atheros wifi

Did you wiki / read the manual? = I've been using the aircrack suite for almost 2 years now, I've used almost every attack except airbase.

ISSUE:

When I attempt to obtain a 4 way handshake and even deauth the client, it fails. This is the only attack that seems to be malfunctioning. any thoughts would help.

---

### Post by tegryan on 2009-10-22
Hi Divider,

Did you ever figure this out?  I have the same situation and connect/reconnect the other laptop, which I see in the Airodump window, but for some reason it never gets the handshake.  I think that's the same thing that's happening to you.

Thanks

---

### Post by shabs on 2011-01-14
Umm.. So did you figure this out? I'm having the same problem :)

---

### Post by shabs on 2011-01-14
Umm.. So did you figure this out? I'm having the same problem :)

---

