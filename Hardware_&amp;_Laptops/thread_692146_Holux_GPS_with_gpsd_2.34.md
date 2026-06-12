---
title: "Holux GPS with gpsd 2.34"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by imbrian on 2008-02-09
I bought a bluetooth GPS reciever for my laptop.  It's a Holux GPSlim 240.  I get the device, am able to pair it without issue, ping the device, etc.  It's working fne...until I try to run gpsd.  There is a problem in the Holux firmware that makes the device "catatonic" if it's written to.  gpsd attempts to make some changes to the device, and everything goes nuts.  Have to drain the battery to reset the internal settings.  An excercise that takes 10 hours.

gpsd 2.35 fixes this by allowing the daemon to be run in "read only" mode.  However, the gpsd that is in the Ubuntu repositories is 2.34.  I attempted to compile it from source but had several errors (I don't remember them and admittedly didn't follow that path for long).  For giggles, I tried installing a deb from Debian and it failed complaining of dependencies.

Has anyone here gotten GPSD 2.35+ working on a current Ubuntu install?  If so, how were you able to do it?

Thanks

---

