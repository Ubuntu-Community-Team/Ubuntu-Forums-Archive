---
title: "Problems with hard drive standby"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Superguppy on 2005-08-03
Hi everybody!

I am using Ubuntu 5.04 on my notebook for 3 weeks now. It all runs fine and i am considering to trash my Windows XP and switch to Ubuntu. But not right now, first I want to test if REALLY everything I want works fine.
There is one really big issue with Ubuntu Linux on my notebook. The hard drive goes to standby mode after only a few seconds (about 10 or 15 seconds). Well, power saving is nice, but this timeout is far too low. And with the hard drive switching on and off all the time my hard drive is in thread of getting damaged.

This is my hdparm.conf file:
```

/dev/hda
{
 	dma = on
 	spindown_time = 60 
	acoustic_management = 254
 	apm = 255
}

```

I tried to read some documentations from hdparm, but it seems I entered everything correctly. What can I do? I want a timeout of 10 minutes, not 10 seconds!!!

In addition here are the specifications of my system:
Harddisk: Hitachi 7K60
Notebook: Fujitsu Siemens D 8820 (2.8GHz, 512MB, ATI Radeon 9000, SiS Chipset)

Best Regards,
Superguppy

---

### Post by scoon on 2005-08-04
Hey there, 

check this out: man hdparm

look at the -S part.

regards, 

scoon

---

