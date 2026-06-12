---
title: "Power Management?"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by Infatuated_iPod on 2006-05-24
Is there any power management application on ubuntu?

My Laptop gets really hot when its plugged in, and when its on the battery it does not hold much of a charge. ( about two hours compared to 4-5 with windows.) 

I think that it is getting hot becuse it keeps on charging after the battery is full.. instead of just sitting there like a good little laptop. 

Btw: Its a dell inspiron 8600.

Any help would be appreciated! :)

---

### Post by Patrick-Ruff on 2006-05-26
the continious charging, I wouldn't think so, the power adapter has its own type of programming, likewise with the battery. but as far as the powermanagement and battery power, I would also be interested to know how to get equal battery life to windows. I mean, with ubuntu breezy on my Inspiron 6000, it would do no such thing, it would be exactly identical to windows. but the battery life didn't do well at all. 

-Patrick

---

### Post by frogotronic on 2006-05-27
[QUOTE=Infatuated_iPod]Is there any power management application on ubuntu?

My Laptop gets really hot when its plugged in, and when its on the battery it does not hold much of a charge. ( about two hours compared to 4-5 with windows.) 

I think that it is getting hot becuse it keeps on charging after the battery is full.. instead of just sitting there like a good little laptop. 

Btw: Its a dell inspiron 8600.

Any help would be appreciated! :)[/QUOTE]

Hello,

  I have a Dell Inspiron 8100 and had similar issues.  I haven't completely solved everything so far, but here's what I have done.

1)  Install GNOME Power Manager via Synaptic Package Manager (and all dependencies).  Then Add to your start-up via the Sessions>Advanced Tab.  Give it a rating of 50.  You can attache dit to the panel and then it will run at start-up.

2)  Install GRKELLM ([http://www.ubuntuforums.org/showthread.php?t=156384&highlight=grkellm)](http://www.ubuntuforums.org/showthread.php?t=156384&highlight=grkellm)).  Try the pre-packaged first.  Make sure to download the DELL insipron plug-in for GRKELLM (via synaptic package manager).

You've have to 'play' with GRKELLM to get it to work.  I haven't tried the latest version - but I'm going to tonight.

Good Luck.

---

