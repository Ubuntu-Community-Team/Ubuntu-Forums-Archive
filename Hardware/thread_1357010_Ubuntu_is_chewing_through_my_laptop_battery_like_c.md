---
title: "Ubuntu is chewing through my laptop battery like candy."
date: 2009-12-16
forum: Hardware
---

### Post by nexus_2006 on 2009-12-16
Any tips to reduce power usage, or even to check the CPU scaling, or limit it manually?  Admittedly, I do keep compiz+avant window manager rolling all the time, so I'm sure that contributes to my problem, but my fully charged battery is being used in less than 1.5 hours.  The same battery/machine runs for around 4 hours on windows watching hulu et. al.

Thanks

Any thing to suggest doing/turning off in addition to making sure power scaling is working as it should and keeping screen brightness down as much as possible?

---

### Post by wojox on 2009-12-16
What happens when you add the Frequency CPU scaling applet to the panel. That will usually let you adjust accordingly.

---

### Post by nexus_2006 on 2009-12-16
When I hover the applet it tells me things are running at 1ghz (this chip is dual core, with 1, 1.3, 1.6, and 2ghz available).  When I try to click, it tells me "Frequency Scaling is not available for the selected CPU."

---

### Post by IcarusR on 2009-12-17
You can disable any hardware you don't use such as bluetooth, wireless in the bios. 
Stop unused services from loading with 'sysv-rc-conf' it's in the repos.

Check out this site for more ideas 

[http://www.lesswatts.org]("http://www.lesswatts.org")

---

