---
title: "Nvidia Black Screen"
date: 2009-12-03
forum: Hardware
---

### Post by jusce on 2009-12-03
I have a Sony Vaio VPCCW14FX with NVIDIA GEFORCE GT230M.
So I tried to install Nvidia drivers and I got a black screen.

So, to acess my system I have to enter "recovery mode" and create a new xorg.conf file, without nvidia drivers on it.

So I cannot load them...

Someone could help me!?

---

### Post by BigMeanMikeRich on 2010-01-08
I just got the same notebook yesterday, had the exact same problem as soon as I enabled the Nvidia driver.  There is a workaround -- I hope you have found it and not given up on running Ubuntu on this notebook!  You can find the details of the workaround here:

[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

You will need a windows installation to extract the EDID information, and a Live CD of some kind so that you can mount your Ubuntu partition and make some changes to /etc/X11/xorg.conf

I am attaching the EDID I extracted from my VPC-CW14FX/W, it should work just fine for yours.  If you have trouble downloading the EDID, or if you have further questions, PM me or better yet hit this thread again so that others can follow along who may be having the same problem.  Good luck!

---

### Post by alonelyva on 2011-04-21
I have the same problem with u... I have the same sony vaio vpcccw14fx...but i got my problem with mac osx??that is ubuntu have the same system with mac osx???
or can u tell me how to run your way in mac osx if know???
thank you...

---

