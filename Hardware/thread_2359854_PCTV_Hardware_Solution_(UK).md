---
title: "PCTV Hardware Solution (UK)"
date: 2017-04-28
forum: Hardware
---

### Post by iankearns on 2017-04-28
Hi there

Am looking for a mobile solution to turn my laptop into a TV and received Freeview channels in the UK. 

Am regularly on the road and utilising my laptop to watch TV makes sense however am not find many linux / ubuntu friendly solutions.

Anyone aware of a dongle or hardware solution that is supported by ubuntu that I can plug an aerial into and get UK channels

---

### Post by tea for one on 2017-04-29
Earlier this year, I purchased this [http://www.dvbshop.net/TechnoTrend-TT-TVStick-CT2-4400-USB-TV-Karte-DVB-C-T-T2-Antenne](http://www.dvbshop.net/TechnoTrend-TT-TVStick-CT2-4400-USB-TV-Karte-DVB-C-T-T2-Antenne)

You have to download the following firmware **dvb-demod-si2168-02.fw**, which has to be added to /lib/firmware

I use w_scan to find the channels and subsequently I use VLC to watch and record live TV (Freeview DVB)

---

