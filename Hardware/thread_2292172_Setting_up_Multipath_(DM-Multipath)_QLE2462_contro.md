---
title: "Setting up Multipath (DM-Multipath) QLE2462 controller -&gt; Sun Storagetek 2540 Array"
date: 2015-08-25
forum: Hardware
---

### Post by Bradley_J_Doern on 2015-08-25
Running Ubuntu 14.04 64bit, and having some problems getting multipathing set up on my fiber controller.  I'm new to this, and still learning, so please dont skip explanation in any of the steps.  :)

The array is currently working (sdb) and mounted (sdb1) while plugged in port 1 of my HBA to port one of the two controller modules on the Sun Storagetek 2540.  When plugging in the second fiber cable, the system usually goes nuts with IO errors.

Is there anyone that would like to school me on the process of multipathing?  This is more for education than necessity, as the array is currently working.  If we want to get deep into it, I do have a second QLE2462 card I can plug in and run 4 physical links to the Sun array...

I've installed DM-multipath and the service multipathd is running.  I've been through the DM-multipath documentation and I must have missed somethign on the install/ config...

Thank you in advance for your time!

---

