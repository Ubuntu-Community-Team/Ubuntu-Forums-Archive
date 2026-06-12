---
title: "Mobile Broadband - Constantly Disconnects!"
date: 2010-11-24
forum: Hardware
---

### Post by slashwannabe94 on 2010-11-24
Hello all, 

My only way to connect to the net is by using a dongle. I use a Huawei HSPDA (T-Mobile) dongle, MODEL: E1750. the speed of the dongle is quite satisfactory and does do the job. but it disconnects itself from the net, every 10 mins. Why... i do not know. it constantly stays on a HSPDA signal, and as you are aware that is a rather fast download rate. 

Also the only way to reconnect is to unplug the dongle itself and then plug it back in. There is a 

if anyone has an idea of why this is happening or how i can fix it please do post! 

Thanks, 

SlashWannabe94

---

### Post by jwmislan on 2010-11-24
You can try to install backport-modules-wireless
you need backports enabled in your  System - Administration - Software Sources

Still Ubuntu 10.04 and 10.10 may disconnect periodically ( seems to be some buggy ongoing wireless problems with ubuntu ?? ) 
I have had success with pinging my router, or my dsl address like follows - 

for my router,  ping with interval ( -i ) of 20-24 seconds 
ping -i 24 192.168.1.1   

same for my dsl 192.168.2.1

just use one or the other not both.
pinging google or other internet domains could aggravate them so don't do that.

Hope it helps 
JWM

---

