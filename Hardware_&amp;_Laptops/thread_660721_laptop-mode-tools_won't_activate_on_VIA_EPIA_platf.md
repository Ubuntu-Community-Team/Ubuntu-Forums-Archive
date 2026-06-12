---
title: "laptop-mode-tools won't activate on VIA EPIA platform"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2008-01-07
I'm using a persistent live USB flash stick with Ubuntu 7.10 on a VIA EPIA EX-10000EG motherboard. I installed laptop-mode-tools in an attempt to reduce writes to the flash drive and increase its life span. However, I can't enable laptop-mode-tools. 

After reading [the FAQ]("http://samwel.tk/laptop_mode/faq"), I changed all ENABLE_LAPTOP_MODE* to 1 in the conf file and called "/etc/init.d/laptop-mode start", but the file /proc/sys/vm/laptop_mode still contains 0, indicating that laptop-mode-tools is turned off.

Is there anything else I could do?

---

