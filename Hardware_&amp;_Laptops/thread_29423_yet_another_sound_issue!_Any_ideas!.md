---
title: "yet another sound issue! Any ideas?!"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by baczoni on 2005-04-24
I've got a Creative CT1745A ISA sound card. Hoary did not recognized it so I added the following line to my ** /etc/modules** file:

**sb io=0x220 irq=5 dma=1 dma16=5 mpu_io=0x3**30

I have system sounds now but I still can't play CD's or music. Games don't have sound either. 
ALSA is loaded during boot process, but the alsamixer gives me the following error:

**alsamixer: function snd_ctl_open failed for default: No such file or directory**

Any sugestions? 

PS: I'm a newbie  :neutral:

---

