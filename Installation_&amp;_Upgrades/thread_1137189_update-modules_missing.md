---
title: "update-modules missing"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by T1000 on 2009-04-25
Hi,

I cannot get any sound since I upgraded from ibex to jackalope.

I downloaded alsa-driver-1.0.19 and alsa-utils-1.0.19 in order to make sure the latest drivers are used.

My problem is alsaconf is failing when trying to run a "update-modules" which is not available.

    case "$distribution" in
    gentoo | debian)
	xecho "Running update-modules..."
	update-modules
	;;

Where could I get it?

Thanks for your help!

---

