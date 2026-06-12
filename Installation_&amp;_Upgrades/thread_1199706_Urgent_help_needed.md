---
title: "Urgent help needed"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by dinkyverma279 on 2009-06-29
Hi,
 
I am using Ubuntu version 8.10 desktop. When i installed ubuntu from CD, it has installed with CONFIG_MODVERSIONS=y
 
Now the problem is i have my own driver, I have built it but the problem is 
 
I have two a.ko and b.ko modules where b.ko has dependency on a.ko. Since CONFIG_MODVERSIONS will append some version information in the exported symbols. So when i am trying to do insmod b.ko, it is reporting me unknown symbol version.
 
I have read one tutorial that i will include modversions.h file in every c file before compilation. I did that but still i am getting the same error.
 
Can some body will tell what should i do to compile the kernel module when CONFIG_MODVSERSIONS is enabled.
 
Regards,
dinky

---

