---
title: "Y570 Wireless Connects, but no internet"
date: 2012-08-20
forum: Hardware
---

### Post by Tach on 2012-08-20
Maybe someone can help me out with this (and maybe someone else will benefit from having the same problem). For some reason, the internet worked during installation, but now it won't. It will connect to the router with the proper password and says it's connected, but when I try to open a web page, it just hangs and times out.

I am getting assigned an IP address by the router, but I noticed I can't ping the router, which I'm sure is related to the problem. The laptop is a Lenovo Y570 and the wireless adapter is Intel WIFI Link 1000 BGN.

Maybe there are some commands I could try to reset everything?

---

### Post by Tach on 2012-08-22
Well, I decided to remove the network manager and use WPA_Supplicant instead. That works really well, although it was a pain in the *** to set up and I had to figure out how to assign an IP address once connected (sudo dhclient wlan0). But it works. I also had to generate a PSK from the paraphrase for the password ([http://www.wireshark.org/tools/wpa-psk.html](http://www.wireshark.org/tools/wpa-psk.html)). I guess this is solved?

I think I'm going to try wicd instead. :/

...um, guess I'll thank myself for the help. Thanks me.

---

