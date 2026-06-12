---
title: "Atheros AR9285 (Wifi) and Atheros AR8132 (LAN)"
date: 2009-07-02
forum: Hardware
---

### Post by Syzothermy on 2009-07-02
Just got my EeePC 1005HA in today, and I was about to install Ubuntu on it. However, there wasn't a driver for either the LAN or the Wifi (both in the title) included in the liveUSB I made. Is there an easy way to install it, like loading it up on the USB drive and running it on the EeePC after installing Ubuntu?

I'd rather not use NDISWrapper if possible, but I guess if I have to I will.

Also, this is Ubuntu 9.04 i386, not the netbook remix. I don't know.. I just don't like the netbook remix layout. But, would the netbook remix have the drivers already?

---

### Post by zepita on 2009-07-02
netbook remix has better driver compatibility with asus eeepc as far as I can tell.

---

### Post by synapsys on 2009-07-02
> Any distribution shipping a kernel >= 2.6.27 will have ath9k present.> **supported chipsets**

 
[LIST]
[*]AR5418+AR5133
[*]AR5416+AR5133
[*]AR5416+AR2133
[*]AR9160
[*]AR9280
[*]AR9281
[*]AR9285 (>= 2.6.29)
[*]AR9102 (AHB) (>= 2.6.30)
[*]AR9103 (AHB) (>= 2.6.30)
[/LIST]
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

9.04 kernel = 2.6.28-13

Not sure what kernel UNR is using but i would assume its the same as Jaunty. I guess you're stuck with ndiswrapper.

---

### Post by Syzothermy on 2009-07-03
> **synapsys said:**
> [http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

9.04 kernel = 2.6.28-13

Not sure what kernel UNR is using but i would assume its the same as Jaunty. I guess you're stuck with ndiswrapper.

Thanks; going by that I decided to try Fedora 11, and it had the drivers I needed. Sorry Ubuntu, maybe I'll use you later. :p

---

### Post by leandromartinez98 on 2009-07-06
If you want to use Ubuntu, the way to make both network
interfaces work is described in my first post of this
thread:

[http://ubuntuforums.org/showthread.php?t=1197614](http://ubuntuforums.org/showthread.php?t=1197614)

---

