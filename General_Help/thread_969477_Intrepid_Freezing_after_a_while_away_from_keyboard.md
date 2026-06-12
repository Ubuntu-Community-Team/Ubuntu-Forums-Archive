---
title: "Intrepid Freezing after a while away from keyboard."
date: 2008-11-03
forum: General Help
---

### Post by dredwerker on 2008-11-03
Hi,

When I leave Intrepid for a fairly long while like overnight or going to work or watching a film, it locks up and doesn't come back. I have turned of powersaving and screensavers so I no longer am only presented with a black screen. The system is just locked.

I have wifi but I am not using it - I am running Ktorrent-kde4 a lot, I wonder if that is it. The only other thing I am running all the time is firefox. I obviously run all sorts of things at other times but that is what I would leave up.

I have never had this on hardy or gutsy.

The machine is dual core 2gig intel. 2gb ram Lots of hard disks. 9800gt nvidia graphics card.

TIA
Dred

---

### Post by dredwerker on 2008-11-03
(forgot to susbscribe)

---

### Post by Peter09 on 2008-11-03
Turn off any screen savers that you have. These can stop the system responding.

---

### Post by garylinux on 2008-11-03
> **Peter09 said:**
> Turn off any screen savers that you have. These can stop the system responding.
Isn't that Kind of broken? Or is that another wonderful kde 4.x "Feature" ?

---

### Post by Peter09 on 2008-11-03
Well this was a well known problem, I'm not sure if it has been resolved, so its worth testing to see if its what is causing your problems.

---

### Post by dredwerker on 2008-11-03
> **Peter09 said:**
> Well this was a well known problem, I'm not sure if it has been resolved, so its worth testing to see if its what is causing your problems.

I have turned off powersaving and any screensavers now. Its just freezing but not if I keep regularly coming back. This doesnt seem to be heat related as for example now is the warmest the computer will get.

---

### Post by dredwerker on 2008-11-04
> **dredwerker said:**
> I have turned off powersaving and any screensavers now. Its just freezing but not if I keep regularly coming back. This doesnt seem to be heat related as for example now is the warmest the computer will get.

I think it is Ktorrent

This is from top
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND

 6177 xxxxxxx   20   0  503m 325m  23m R   97 16.1 125:06.07 ktorrent

So cpu usage is at 97%.

Does that mean Ktorrent is broken?

---

### Post by dredwerker on 2008-11-04
> **dredwerker said:**
> I think it is Ktorrent

This is from top
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND

 6177 xxxxxxx   20   0  503m 325m  23m R   97 16.1 125:06.07 ktorrent

So cpu usage is at 97%.

Does that mean Ktorrent is broken?

Just found a launchpad bug for this very thing in case anyone else has the same problem.

[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/285807](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/285807)

---

### Post by dredwerker on 2008-11-21
> **dredwerker said:**
> Just found a launchpad bug for this very thing in case anyone else has the same problem.

[https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/285807](https://bugs.launchpad.net/ubuntu/+source/ktorrent/+bug/285807)

Ktorrent part solved by upgrading to 3.1.4 but lockups still happen.

---

