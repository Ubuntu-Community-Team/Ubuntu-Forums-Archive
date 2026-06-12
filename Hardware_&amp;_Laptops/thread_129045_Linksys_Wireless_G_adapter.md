---
title: "Linksys Wireless G adapter"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by iMac on 2006-02-12
I used Ndiswrapper to install the driver for my Linksys Wireless G notebook adapter, and I can't connect to my network. I can see the adapter listed in the Network Settings, and i activated it. I used WiFi -radar to find my wireless network and entered the WEP key, and i chose to connect, but it just says "working" forever and never connects. Does anyone know what I am doing wrong?

---

### Post by nanotube on 2006-02-13
hmm, i cant be sure what exactly your problem is, but my experience with wifi-radar has been less than good. it would just fail to connect fairly frequently... 
read this section of my howto, maybe it will help:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles)

---

### Post by K.Mandla on 2006-02-13
I had to use ndiswrapper and ndisgtk+ to install a wireless connection on a Dell laptop, and the thing that I remember most is that it took a VERY LONG time for it to sign on to my router. I switched from static to DHCP in the network settings, and then it sat and sat and sat ... and then finally, it came alive.

Luckily, that only happened the one time, when I first installed it. Now the connection pops into place immediately.

I don't know if that sounds like your problem, but if it is, my advice (for what it's worth) is ... be patient.

---

### Post by iMac on 2006-02-13
ok, thanks, i'll give it a try!

---

