---
title: "Dual Core Compliant?"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by CadMasterAdam on 2006-08-01
I have  an Intel D 930 processor, and now that i am on Dapper Drake 6.06 full time i notice that the system monitor only shows one CPU historgram window.

does this mean that Ununtu only see's one chip? or does it use both, but the Sytem monitor need a little tweeking to show both cores?

thanks ya'll

---

### Post by Jagot on 2006-08-01
The default kernel supplied with Ubuntu does not support dual core, multiple processors, hyper-threading, etc.  You need ths smp kernel.  From Terminal:

```
sudo aptitude update
sudo aptitude install linux-686-smp
```

After it is installed, restart as it tells you to then when you reboot you will notice you have 2 CPUs showing in the system monitor.

---

### Post by CadMasterAdam on 2006-08-01
thanks jagot,

then does that mean, sofar i'm not taking advantage of the dual cores?

and also will this make a difference; makign ubuntu see two processors?

anyones previous experiance would be great to this noob

---

### Post by Jagot on 2006-08-01
I think that before installing the new kernel you would not be taking advantage of the two cores.  I have Hyper-Threading as opposed to dual core and HT is frankly crap - not too much difference, but with dual-core it might be better, but I don't have any experience with it.

Best way to find out is give it a go!

---

### Post by bbzbryce on 2006-08-01
> **CadMasterAdam said:**
> I have  an Intel D 930 processor, and now that i am on Dapper Drake 6.06 full time i notice that the system monitor only shows one CPU historgram window.

does this mean that Ununtu only see's one chip? or does it use both, but the Sytem monitor need a little tweeking to show both cores?

thanks ya'll

I'd personally install amd64 as that is what I'm running on my Intel Pentium D 805.  Both cores show up in the system monitor.  Of course with the 64 bit you'll run into problems with some software, but with a little work you should be good to go.  I got a 32 bit version of firefox that has flash plugins and what not.  I also was able to get compiz/xlg mostly working in about 20 minutes.

---

### Post by CadMasterAdam on 2006-08-01
thanks ya'll i'll giver a go @ home

---

