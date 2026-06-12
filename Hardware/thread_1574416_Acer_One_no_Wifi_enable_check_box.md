---
title: "Acer One no Wifi enable check box??"
date: 2010-09-14
forum: Hardware
---

### Post by iamgeniusrnti on 2010-09-14
So I installed Ubutnu Ultimate 2.4 on my SECOND netbook and it totally refuses to give me the option to enable wirelss.
 
In the hardware box it has two choices for broadcom drivers but neither work even though they said they were activated.  After disabling both, I followed the advice found here and tried the ath5k methhod--no avail.
 
Here's the kicker, it worked fine in Live mode and it installed perfectly on my other Netbook.  This has to be a stupid problem, but I just don't know where to start:(
 
Reinstall?

---

### Post by timewaves on 2010-09-14
I'm having the same problem, except it just broke for some reason.  I would uninstall if I were you.

---

### Post by sisyphus1978 on 2010-09-14
I have an Aspire One ZG5. I found upgrading to the maverick backports helped give me stable wireless on Lucid.

> sudo aptitude install linux-image-generic-lts-backport-maverick


---

### Post by iamgeniusrnti on 2010-09-24
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)
 
Turned out although I have tow other Acer Ones, this particular model which I thought was the same as my other two is different. It uses a Broadcom Wifi and Linux has to think really hard before using it.

---

