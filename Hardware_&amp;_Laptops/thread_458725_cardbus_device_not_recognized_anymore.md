---
title: "cardbus device not recognized anymore"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by xzero1 on 2007-05-29
The first time I inserted my Dlink DWLG650 cardbus card, a restricted driver message shows. I got it working but my system locked up quickly, Checking the syslog helped me to debug the problem. Finally by turning on my internal wi-fi card it seemed stable. I used it for 2 hours straight with no problems.
Now after a couple of reboots the card is no longer detected. Checking restricted drivers manager : 'Your hardware does not need any restricted drivers". In syslog (at the time it was detecting) there is the line "...ath_hal: module license 'Proprietary' taints kernel". The computer is a Toshiba 3500 tablet pc using the latest ubuntu 2.6.20-16 generic kernel. What gives?

---

