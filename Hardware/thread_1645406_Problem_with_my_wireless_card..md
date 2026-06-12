---
title: "Problem with my wireless card."
date: 2010-12-14
forum: Hardware
---

### Post by disconnections on 2010-12-14
My wireless card had been working perfectly for ages but it just decided that unless I am literally less than six inches away it won't detect any wireless signals.

I'm not sure if this is the right place to do this

but it is really bothering me and I'd like to know if I can fix it without getting a new wireless card.

---

### Post by cipherboy_loc on 2010-12-14
When you are less than six inches away, does it detect it at full power or some lower power? Also, have you changed anything with iwconfig or ifconfig? 



Cipherboy

---

### Post by cipherboy_loc on 2010-12-14
Also, what is the type of the wifi card? You can find it with:

```
lspci | grep -i 'network' 
```



Cipherboy

---

### Post by disconnections on 2010-12-15
sorry i took so ridiculously long to reply. Internet was down. :-|

It will generally stay at full power if I'm that close. This is just a very recent thing that has happened and I don't believe I have done anything to cause this. I mean, maybe my wireless card is just shot, but I don't see why it would do that so randomly.

 Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by danellisuk on 2010-12-15
Similar issue here.  Dell mini 9 with BCM4312 has been working fine with Ubuntu 10.04 since April.  I have a feeling it hasn't been working for a week or so, but I didn't take much notice until last night when I decided to properly investigate.  Tonight I have turned off all potential interference and Removed/Re-enabled Broadcom STA driver.  Rebooted access point (D-link DAP 1160).

Tonight after reading the last post I tried putting the netbook right next to the access point and I'm now getting 54mb connection.  Downstairs is getting less than 2mb, whereas that would normally be 54mb.
I keep thinking interference, but cannot figure out what.

I'm finishing for tonight; tomorrow evening I will test with another laptop (to test access point) and also try a fresh Ubuntu install on another partition.

---

