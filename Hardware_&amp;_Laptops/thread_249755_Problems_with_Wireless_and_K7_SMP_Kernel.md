---
title: "Problems with Wireless and K7 SMP Kernel"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by reedatschool on 2006-09-03
Alright the problem is that there is a conflict with a IRQ (In my case #233) that causes this issue.  I got this from a post I read here which had my basic problem.

[http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/5820](http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/5820)

Here are the important bits

> I am having problems with an Ubuntu K7, 32-bit, SMP kernel (2.6.15-25) 
> and ndiswrapper.  When I first boot up the machine ndiswrapper works 
> correctly but after a few minutes (please note that the time varies) my 
> wireless network connection stops working.  This problem only occurs 
> when I use the K7 SMP kernel.  When I use the standard 386 Ubuntu 
> kernel, I do not experience the problem.

And then

"I remember reading about a similar problem recently, but could not find  the reference. The essential part of the problem in that case was a shared IRQ, with the other device not answering its interrupts and the cpu finally disabled the IRQ, just as happens for your system. Check dmesg to see if another device is using IRQ #233. On your uniprocessor system, I would guess that the IRQ is not shared."

I have also seen numerous posts on this issue

[http://www.ubuntuforums.org/showthread.php?t=205876](http://www.ubuntuforums.org/showthread.php?t=205876)

[http://www.ubuntuforums.org/showthread.php?t=81723](http://www.ubuntuforums.org/showthread.php?t=81723)

and many others.  

Is anyone aware of fix or work around for this problem (other than just using 386 kernel)?  

Reed Harding

---

### Post by reedatschool on 2006-09-05
Alright after poking around a little more I found out this is not just a problem with the SMP K7 kernel, but also with the regular K7 kernel.  Anyone know a way to avoid this IRQ conflict?

Reed Harding

---

