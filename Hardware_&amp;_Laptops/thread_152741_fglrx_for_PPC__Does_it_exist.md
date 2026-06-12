---
title: "fglrx for PPC?  Does it exist?"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by nuzzy on 2006-03-30
Hi,

I have a PowerMac with a Radeon card.  It uses the "ati" driver.  I searched Synaptic for the fglrx driver but it doesn't seem that it exists.  Does anyone know of a substitute or another solution for this?

---

### Post by benvdh on 2006-03-30
Hey,

The fglrx drivers are not in synaptic for PPC users, since ATI hasn't released the linux FGLRX drivers for PPC. Since you're a dapper drake user you could try to enable the EXA rendering architecture which is a new feature of Xorg since version 6.9 . But you will need to use the radeon driver instead of the ati driver, which is still unsupported. Have a look at the following page :

[http://xorg.freedesktop.org/wiki/ExaStatus]("http://xorg.freedesktop.org/wiki/ExaStatus")

When you're finished configuring, hit ctrl-alt-backspace to restart X and see if it works,

Regards,

Ben

---

### Post by nuzzy on 2006-03-30
Thanks Ben.  I'll give it a shot.

---

