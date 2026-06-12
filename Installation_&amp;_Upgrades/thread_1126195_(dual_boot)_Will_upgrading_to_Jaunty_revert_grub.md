---
title: "(dual boot) Will upgrading to Jaunty revert grub?"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by thomasboleyn on 2009-04-15
Hi there. I currently run a dual boot setup on my Sony Vaio NS20E ([http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-NS20E/S&site=voe_en_GB_cons&pageType=Overview&category=VN+NS+Series](http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-NS20E/S&site=voe_en_GB_cons&pageType=Overview&category=VN+NS+Series)) with Xubuntu Intrepid and Vista Ultimate. I installed Xubuntu after Vista (far too difficult to do the other way round) and edited the grub file so that it just says:

Xubuntu
Windows Vista 

with a 10 second timeout when I boot. My question is if/when I upgrade to Jaunty, will this revert to something resembling it's original state, also what boot options will I be offered when I boot after upgrading?

Any help would be greatly appreciated, thanks.

---

### Post by kpkeerthi on 2009-04-15
If you upgrade using the update-manager, you should be OK. The GRUB will be upgraded and you should see a new kernel line at the top.

---

### Post by thomasboleyn on 2009-04-15
> **kpkeerthi said:**
> If you upgrade using the update-manager, you should be OK. The GRUB will be upgraded and you should see a new kernel line at the top.

And then I can just edit the grub file in mousepad/gedit again to tidy it up?

Thanks for the reply.

---

### Post by kpkeerthi on 2009-04-15
Yes.

I suggest you follow the cleanup instructions here: [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by thomasboleyn on 2009-04-15
> **kpkeerthi said:**
> Yes.

I suggest you follow the cleanup instructions here: [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Thanks for replying. I did that before so it'll be easy to repeat.

---

