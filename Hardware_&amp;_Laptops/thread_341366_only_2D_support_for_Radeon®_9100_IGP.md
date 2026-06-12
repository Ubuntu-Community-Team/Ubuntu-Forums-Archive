---
title: "only 2D support for Radeon® 9100 IGP?"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by manutdfan2850 on 2007-01-18
Hello,

I am running Ubuntu Dapper on my Toshiba Satellite A75-S206 Laptop (purchased about 3 years ago). It has a ATI Mobility Radeon 9000/9100 IGP video.  I installed the drivers from ATI, and the most recent drivers that support my card is 8.26.18. Now having installed ATI's drivers, I've learned that these set of drivers DO NOT support 3D. Please see the text from ATI's Linux Driver Release Notes below : 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html)

```
ATI Integrated Product Support

The ATI Proprietary Linux driver is designed to support the following ATI Integrated products:
Radeon® Xpress 200 series
	Radeon® 9100 IGP
Radeon® 9200 IGP
	Mobility™ Radeon® 9000 IGP series
Mobility™ Radeon® 9100 IGP series
	
[B][U]
	Caution: 	This software driver provides 2D support only for the ATI Radeon® 9100 IGP and ATI Radeon® 9100 PRO IGP.[/U][/B]](*,) 

```

My question is, do I have other options besides the ATI drivers for my ATI Radeon 9100 IGP to enable 3D support? I dont care if they are not official ATI drivers as long as they work.  I would like to install and try out Beryl and be able to play a few games which is why i need 3D support. 

Please help me out. Thanks in advance.

---

### Post by tbeld on 2007-01-18
Try this: [http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)

---

### Post by residualbit on 2007-05-08
same problem, same card...has anything been updated since this little tutorial? i'd rather not use dapper packages to fix a problem in feisty...

---

### Post by phazei on 2007-10-07
has anyone been able to get beryl or compiz to work with the ATI 9100IGP?
I've been looking around and can't seem to find a solution.  The last of ATI's linux drivers to support the 9100IGP was 8.28.8...
help? or sol?

---

