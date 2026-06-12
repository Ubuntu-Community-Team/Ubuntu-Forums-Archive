---
title: "enabling laptop mode tools"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by canardo on 2006-09-19
Hi,

In my endeavour to get a decent battry life out of my Compaq N410c, I have been reading up and one thing that keeps coming up is to enable laptop-mode-tools 

now this might seem odd but how do I do this i have looked in /etc/acpi and found nothing or is it somewhere else

is there a wiki on how to improve battery life in Ubuntu

---

### Post by canardo on 2006-09-19
ok the setting is in /etc/default/acpi-support

ENABLE_LAPTOP_MODE = true

---

### Post by Donshyoku on 2006-10-18
What in particular does this do?  Throttling?  Optimizing? Disabling devices?

I have a Compaq V2000 and I get about 1:30 less battery life in Ubuntu than I did in XP.  I really want to improve this.  My 12-cell battery with half brigthness only lasts about 2 hours in my laptop!

The only concern is that none of my parts support throttling, so if this is a throttling application, I may not need the package.

---

### Post by Eddie Hung on 2006-10-27
I believe the only thing it does is spin down your hard drive in order to conserve power:

[http://www.thinkwiki.org/wiki/Laptop-mode-tools](http://www.thinkwiki.org/wiki/Laptop-mode-tools)

I've searched this forum in the past - but not had much luck - does enabling this setting improve battery life significantly? 

Can the previous n410c owner report back, please - I have a n410c too!

Thanks,

Eddie

---

