---
title: "Radeon 9200 SE card is not working!"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by Grog140 on 2006-07-20
A buddy of mine and I are on our last ropes trying to get this thing working. He can't boot Ubuntu while his 9200 SE card is enabled. It ALWAYS freezes while loading hardware drivers.

So he can only get into Ubuntu with his less than stellar integrated intel one. We have been trying everything to get this working and have crashed the system completely 3 or 4 times and had to reinstall.

Doing a "lspci | grep ATI" picks up his card, but there is no section device in the xorg.conf. 

I have no idea what to try next. Can anyone help? Or point me in the right direction?

thanks in advance.

---

### Post by Grog140 on 2006-07-20
Alright, we got it past the loading hardware drivers. We had to blacklist the intel card. So we got past the freez point and now it isn't loading the X server.

I am guessing its because the Radeon 9200 SE isn't in the xorg.conf file. The question I have now is how would I put it in and make it work? The output to lspci is:

```
40:01:02.0 VGA compatable controler: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

40:01:02.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```

---

