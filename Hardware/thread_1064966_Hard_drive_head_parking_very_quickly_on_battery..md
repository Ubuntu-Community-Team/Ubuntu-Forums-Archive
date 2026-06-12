---
title: "Hard drive head parking very quickly on battery."
date: 2009-02-09
forum: Hardware
---

### Post by stchman on 2009-02-09
Hello all, I am running Hardy on my Toshiba laptop.  I implemented this fix:

[https://wiki.edubuntu.org/PowerManagement](https://wiki.edubuntu.org/PowerManagement)

Look under the Hardy 8.04 section.

This fixed the excessive load cycle count on the laptop while it is on AC.

When I unplug the laptop and let it run on battery power the hard drive spins down in under a minute.  It does not spin back up so the load cycle count does not increase while idle, but it does increase through usage.

My question is what parameter in a .conf file do you modify to set the spindown to say (5) minutes of no activity on battery.  I mean a near immediate spindown is excessive.

Thanks.

---

### Post by stchman on 2009-02-10
Anybody have any input?

I was wondering if the /etc/laptop-mode/laptop-mode.conf file.  There appear to be a lot of settings in that file.

---

