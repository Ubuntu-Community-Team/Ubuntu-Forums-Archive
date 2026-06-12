---
title: "Can't Get WiFi to work!!! Please help. Been trying all day."
date: 2010-06-26
forum: Hardware
---

### Post by Hexeir on 2010-06-26
I am putting ubuntu on an eeepc 1000HD. I originally put ubuntu 10.4 on it, the wifi was performing very poorly. Someone told me to put eeeBuntu on it because the wireless module is programmed specifically for this hardware, so I did. The wireless didn't work at all. No networks were detected. So I updated, and it updated all the 9.10 stuff, and it looks like it removed a bunch of what made it eeebuntu in the first place. Still no WiFi. I run lstpci and it does show the wireless card. 

Confused. Anyone have any hints?

Thanks!

---

### Post by Algot Runeman on 2010-06-26
For what it's worth, I installed Kubuntu 10.04 (KDE Desktop) on my Asus 1101HAB netbook and WiFi works great. As far as I can tell my only headache is NO sound. Posted elsewhere for that issue.

---

### Post by Hexeir on 2010-06-26
Feh, I have a Xubuntu disc,also... I could give it a shot... I have a broken package I can't fix anyways. Might as well. I'll let you know how it goes. Thanks.

---

### Post by wilee-nilee on 2010-06-26
> **Hexeir said:**
> Feh, I have a Xubuntu disc,also... I could give it a shot... I have a broken package I can't fix anyways. Might as well. I'll let you know how it goes. Thanks.

What you need to do is identify the card run in the terminal. This will list all the haedware in your computer
```
lspci
```

With identifying the card and knowing the driver needed if thats the problem any distro should work.

Also wifi working poorly what does that mean, in a relative way to what?

---

