---
title: "Evolution Send and Receive slow under 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by cprofitt on 2009-10-31
I have noticed that checking email under 9.10 using evolution involves a deley of 30-45 seconds before evolution checks email.

A)  Has anyone else noticed this?

B)  Does anyone know what the issue might be?

Thanks

---

### Post by plan9z on 2009-11-10
Ubuntu 9.10, Evolution 2.28.1
I too have noticed a similar delay in Evolution.  Also images in Evolution html mail are extremely slow to download and sometimes time out.  I originally had delay problems in Firefox, but turning off IPV6 in Firefox and via the "ipv6.disable=1" addition to GRUB startup fixed the delay. I also have proxy turned off in Evolution Network and have selected "Direct connection to Internet" in EDIT>PREFERENCES>NETWORK>PROXY SETTINGS.

Does Evolution have a built in reference to IPV6 that may be causing delays?

What else needs to be done?  The delay is very frustrating.

--Ben

---

