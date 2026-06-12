---
title: "How do I install/use open-source ATI drivers?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jimmyboy09 on 2009-04-26
Hallo der.  

I have an ATI Mobility FireGL V5700 vid card on my laptop.  After upgrading to jaunty, I initially installed the proprietary ATI driver (fglrx) and consequently, my laptop did not work.  So I uninstalled the proprietary driver, and here I am.

After looking through many threads, I **[U]think[U]** that I have two options:
1)  Manually install the restricted driver (Catalyst 9.4) from ATI's website via download & deb.
2)  Just go ahead and use the open-source driver by changing the xorg.conf file so that the "Device" section specifies using driver "ati"

So first, are these two options even viable ones?  And if so, which is the better route?  I'm not exactly dying to use compiz again, but life on the dull side seems pretty boring right now :)

---

### Post by s3lekta on 2009-04-26
someone said on here to try this -->

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

---

### Post by jimmyboy09 on 2009-04-27
The thing is, I have no idea if that is really a viable option.  Is the end result of a manual install the same as that of the synaptic install?

If it isn't, then great.  I'd go ahead and do it.

But if they end up doing the same thing, then I'd need to know how to revert.  Would the revert be similar to that of removing the synaptic-installed driver (apt-get remove --purge xorg-driver-fglrx)?  Or would it be completely different?  

I'd rather go do anything that I cannot fix.

But thanks.

---

