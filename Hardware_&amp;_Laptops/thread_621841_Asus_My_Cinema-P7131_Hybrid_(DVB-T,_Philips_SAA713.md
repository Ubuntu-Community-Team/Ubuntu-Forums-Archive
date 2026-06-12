---
title: "Asus My Cinema-P7131 Hybrid (DVB-T, Philips SAA7131E)"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by arthur_8200 on 2007-11-24
Hi!

I have been using a Terratec Cinergy (USB) XS for more then a year (with v4bl-expereminteal) and now I want to use the Asus My Cinema-P7131 Hybrid (only DVB-T) @ Ubuntu 7.10 amd64.

The first time I boot my system with the asus P7131 I copied the right firmware (```
sudo cp dvb-fe-tda10046.fw /lib/firmware/'uname -r'
```) and restarted. The card was recognized
(lspci ```
Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```) proper and I also got a dvb-device (```
arthur@arthur-ve3200:~$ ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net
```0). I think at this time it already would have worked well.
So I just tried watching tv but I always used the wrong frequence :mad: and had no signal. Due to this I thought there must be something wrong and I tried everything which cross my mind (v4l-dvb and v4l-dvb-experimental).
Now I haven't got any dvb-device :(. Maybe because I tried so much and my kernel is bad?

How can I remove all the v4l-dvb stuff?

Thank you very much!!!!

---

### Post by arthur_8200 on 2007-11-27
Of this problem I reinstalled my system. After doing this I just copied the firmware (sudo cp dvb-fe-tda10046.fw /lib/firmware/), restarted and everything was fine. :)

---

