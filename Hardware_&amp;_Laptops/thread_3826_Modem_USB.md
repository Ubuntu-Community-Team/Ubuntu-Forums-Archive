---
title: "Modem USB"
date: 2004-11-09
forum: Hardware &amp; Laptops
---

### Post by larry on 2004-11-09
Hi Everybody,
I am a newbie and so far I have tried only Mandrake linux (it did not perform very well on my laptop) and Gentoo on my desktop (works fine, but I needed a friend to set it up...a very complicated business).
I would like to give Ubuntu a try, but I first need to know if that kind of USB modem I have at home (aethra um1020) gives any hardware recognition problem. I would not like to fight by myself to set up the internet connection.
Thanks to anybody who can help.
Larry

---

### Post by astoltz on 2004-11-10
Well I am by no means an expert but I just fought with my USB modem for a while and can tell you that it wasn't pretty.  My modem uses the generic cdc_acm kernel module as a driver and I think that's where the problem lies.  Don't know what driver your particular modem uses.  I've read some success stories from people using a speedtouch usb modem but apparently there is a speedtouch driver that is working.

What worked in the end, was installing a new kernel re-compiled from source.  I actually installed a 2.6.7 kernel (Warty has 2.6.8).  I'm not smart enough to figure out exactly where the problem was and it may have been able to be fixed with a less drastic measure, but the new (old) 2.6.7 kernel is working just peachy and the modem works too...

Don't let that scare you away from ubuntu though as, like I said, I think it is a problem with the cdc_acm module that is shipping with 2.6.8 kernels, not with Ubuntu itself.  Good luck...

---

