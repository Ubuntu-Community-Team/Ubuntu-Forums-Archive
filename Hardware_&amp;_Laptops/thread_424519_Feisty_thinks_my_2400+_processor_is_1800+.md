---
title: "Feisty thinks my 2400+ processor is 1800+"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by ftmichael on 2007-04-26
The subject line kind of says it all here.  Hoary, Breezy, Dapper, and Edgy all recognised my processor as the Athlon 2400+ it is, but since I upgraded to Feisty, everything is telling me it's an 1800+.  And my system is much slower now; Gaim/Pidgin in particular is sopping up over 70% of the processor and taking forever.  I have no idea what the issue is; I've never heard of this sort of thing happening to anyone else.  Thoughts?

**EDIT:** It has come to my attention that I perhaps have the wrong kernel installed, because I did a manual upgrade to Feisty instead of using the Update Manager like a good boy.

> michael@jeezychreezy:~$ uname -a
Linux jeezychreezy 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

I have the -386 kernel installed, as you see, when I believe I wanted -generic.  How can I fix this now?  Update Manager says my system is up-to-date, understandably.

According to Synaptic, linux-generic 2.6.20.15.14 is installed, as well as linux-386 2.6.20.15.14.  linux-image-2.6.20.15-generic is also installed, as are linux-image-386 and linux-image-generic and linux-restricted-modules-generic.

Michael

---

### Post by wersdaluv on 2007-04-26
I'm experiencing the same thing. When I upgraded to Feisty from Edgy using the official method, Kubuntu and Ubuntu says that my computer is i686. When I did a fresh install of Kubuntu Feisty from the i386 live CD, Kubuntu claims that my machine is i686. 

This is so odd. What will happen to my system if my processor is not properly recognized?

---

### Post by ftmichael on 2007-04-27
I rebooted and selected the -generic kernel in the grub menu (press Esc at the start of your boot to load grub).  I then removed the -386 kernel.  This helped with the speed, but the system still thinks my processor is 1800+.  I *swear* it's 2400+!  I'll have to see if I saved the original packaging somewhere.

Michael

---

### Post by dhaus111 on 2007-04-28
In order to run those kernels you have installed you have to boot to them with grub.  but be aware if you use nvidia you need to get the linux-restricted-modules package for your kernel and you'll need to reinstall the nvidia-glx-new.

there should be entries in the menu.1st aleady

---

