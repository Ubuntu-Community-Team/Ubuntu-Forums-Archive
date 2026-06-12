---
title: "It is not detecting the wireless card"
date: 2008-08-21
forum: Hardware
---

### Post by techie_india on 2008-08-21
Hi,
Ubuntu 8.04 not able to detect my Wireless card ,
I have done :

```
sudo lspci | grep -i network
it shows : 0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

I have Dell laptop vostro 1400 series
```

But the blue light of WiFi is on.

Im a newbie.
Can anybody help how to configure the wireless card

Thanks and regards
Anshuman Srivastava

---

### Post by sergiom99 on 2008-08-22
Try this howto, read the wireless section.
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
Its for a BCM4311 and works like a charm in my BCM4328 too.
Good luck.

---

### Post by twinkel1961 on 2008-08-22
I had the same problem but solved it with the extensive info on
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff). It does describe how to get your BCM4310 working using ndiswrapper.

good luck

---

