---
title: "2G SD card nightmares"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by xhantt on 2006-10-26
Recently I bought and 2G SD card, and everything I tried to use it in Edgy failed.

The builtin card read is a Texas Instruments, loading module tifm_sd I can read 1G and 512M just fine, but can't mount 2G card.

I try an Myson CS8819A2 USB SD adapter, again it just read fine 1G and 512M, I can see the root of the 2G card but can't access the files or folders.

Also both TI builtin reader and USB adapter work fine under XP.

---

### Post by darkshadow on 2006-11-27
2GB cards will start working fine if you self compile kernel 2.6.18. The new kernel should get all card readers working.

When I did it I found the tifm modules where not part of the kernel so you will have to self compile them also here is the link
[http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver)

---

