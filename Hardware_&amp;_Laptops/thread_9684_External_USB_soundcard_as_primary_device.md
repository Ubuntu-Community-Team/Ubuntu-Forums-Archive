---
title: "External USB soundcard as primary device"
date: 2004-12-30
forum: Hardware &amp; Laptops
---

### Post by twisted_steel on 2004-12-30
I have an external USB sound card that is detected properly when I plug it in, but I am wondering if there is a way to have it changed to the primary sound card whenever I plug it in.  Currently I am killing esd and then in a terminal running
```
esd -d /dev/dsp2
```I read that I can change the default sound card all the time by adding it in /etc/esound/esd.conf, but I won't necessarily have the USB card in there when I boot.  I'd also like to keep my onboard sound enabled.  Perhaps there is a better way to do this?

Thanks.

---

### Post by 7marius on 2007-11-09
I use this workaround:
[http://ubuntuforums.org/showthread.php?p=3735633#post3735633](http://ubuntuforums.org/showthread.php?p=3735633#post3735633)

---

