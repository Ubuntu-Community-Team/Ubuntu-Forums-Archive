---
title: "Acer Aspire 7750G and slow wifi"
date: 2011-09-19
forum: Hardware
---

### Post by nampat on 2011-09-19
Hello,

I have a problem. Only reason that is keeping me switching from Win to Ubuntu is slow wifi problem. I have Acer Aspire 7750G with Atheros wireless card. Wifi was very slow on Ubuntu 11.04 and is the same in 11.10 Beta 1. 

I have read a lot of threads about that problem and tried different things like balcklisting acer-wmi, using command iwconfig wlan0 power off, creating ath9k.conf file for encryption thingie and disabling IPv6 - absolutely no luck. What else can I do to solve this problem? Nowadays you just don't want to use Ethernet cable as workaround anymore.

I was waiting for new Ubuntu release and hoping that it will solve the problem, but it doesn't. Is there any other solution I can try? I can't find any from internet.

---

### Post by nampat on 2011-09-20
I did clean Ubuntu 11.10 Beta install yesterday - still the same problem. I also tried Fedora 15 just to see how it works - same problem existed there too. At first Wifi is very fast, but after some minutes it gets slower and slower. It dosen't disconnect, but I have to refresh webpages several times before I can access them. Pages load very slowly. It seems that when I disconnect wireless and after that reconnect, then wifi is fast again for couple of minutes.

I am out of ideas... :(

---

### Post by nampat on 2011-09-26
Bump! :)

---

### Post by k3nc on 2011-09-29
I have same issue on Acer 7750g with Atheros chipset.
when it works "fast" max speeds of 2.2MB/sec

must admit. after upgrading to 11.10 the connection became much more stable, but still not constant.
works fine under windows and speeds of 14MB/sec on same network

---

### Post by nampat on 2011-09-30
Same problem - I have tried using Windows 7 and Wifi is fast. Maybe it is a little bit better with 11.10, but I have to say it is still very very annoying and sadly noone from community can help. It is a real deal killer for me at the moment :(

---

### Post by djodjooo on 2011-12-05
Hello I am hesitant to buy this pc.

ACER ASPIRE 7750G-2678G75MN
[http://fr.acer.be/ac/fr/BE/content/model/LX.RCX02.126]("http://fr.acer.be/ac/fr/BE/content/model/LX.RCX02.126")
Or
Aspire AS7750G-2674G87MN
[http://fr.acer.be/ac/fr/BE/content/model/LX.RCX02.120]("http://fr.acer.be/ac/fr/BE/content/model/LX.RCX02.120")

The problem is still present with Ubuntu 11.10 final?

Y is there any other problems?
I found this [https://friendly.ubuntu.com/11.10/Acer/Aspire%207750G/I:Euk0qp:GsV:BEG:Us:BEfp:k:B5G:Ovk:BF7/]("https://friendly.ubuntu.com/11.10/Acer/Aspire%207750G/I:Euk0qp:GsV:BEG:Us:BEfp:k:B5G:Ovk:BF7/")

Thank You !

---

### Post by nampat on 2012-03-02
Since today I am using Ubuntu 12.04 Beta 1 - everything works like a charm. Wifi is as fast as it is on Windows. That can mean only one thing - Windows has to go! :)

---

### Post by nampat on 2012-03-06
back in the beginning...somehow my wifi is slow again. Thinking what should i do...

---

### Post by richdup on 2012-03-09
Nampat,

I have a laptop similar to yours and had the same problems. After trying different things I finally found something that works, hopefully for the long run.

I simply installed Wicd Network Manager from the Ubuntu Software Centre, then disabled networking in Network Manager (simply click on the network icon in your toolbar and uncheck "enable networking"). Then use Wicd Network Manager to configure your wifi, and voila!

Hope it works for you too. Enjoy.

---

### Post by nampat on 2012-03-09
I am glad to hear that you have found the solution. I'll try it later today and let you know, how it works!

---

### Post by nampat on 2012-03-10
It really seems to work! Thank you for the tip!!! :) Finally I can move to Ubuntu 100%.

---

### Post by nampat on 2012-06-16
Actually this problem drives me mad! Everything was working fine until today I installed updates and got new kernel:  Linux 3.2.0-25-generic-pae. After that Wifi was unusable - extremely slow. I switched back to previous kernel just minutes ago and everything works fine again, but does it mean that now I am stuck with older kernel and that is it??? How is it possible that this problem was fixed and broke again?

---

