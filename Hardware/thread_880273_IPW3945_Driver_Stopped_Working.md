---
title: "IPW3945 Driver Stopped Working?"
date: 2008-08-04
forum: Hardware
---

### Post by hxczach on 2008-08-04
So after having lockup issues with Hardy, i decided to move back to Gutsy(7.10). On first start-up the ipw3945 drivers worked fine, and i was able to connect to my wireless network. But after installing my ATI Drivers(32 Bit v 8.7) for my Video Adapter, the ipw3945 don't appear to be starting. "iwconfig" doesn't show any adapters. Is there a way to fix this, or possibly upgrade to iwl3945 drivers? If i tried to switch to the iwl drivers, would there be a computability issue with the Gutsy kernel?

Any help is much appreciated.

---

### Post by phidia on 2008-08-04
In searching the ipw3945 driver and gutsy I came across [this page]("http://build2be.com/en/content/enabling-ipw3945-without-ipw3945-kernel-driver") it seemed related but maybe I'm wrong. 
I hope it helps.

---

### Post by hxczach on 2008-08-04
Yeah im not to sure of what to do.
I'm trying to find a tutorial about how to upgrade from ipw3945 to iwl3945 in Gutsy.

---

### Post by phidia on 2008-08-04
> **hxczach said:**
> Yeah im not to sure of what to do.
I'm trying to find a tutorial about how to upgrade from ipw3945 to iwl3945 in Gutsy.

I realize that. Maybe the only way you can do that is to upgrade your kernel and from what I've seen (and what you said about going back to Gutsy) there are quite a few bug reports against the Hardy kernel.
That's why I included that link it seemed related to getting the ipw3945 working again.

---

### Post by hxczach on 2008-08-05
This may sound dumb, and if it is don't pick on me. (im teh linux n00b) But could my kernal headers have anything to do with my wireless network cards drivers failing to load?

---

### Post by Daelyn on 2008-08-06
> **hxczach said:**
> This may sound dumb, and if it is don't pick on me. (im teh linux n00b) But could my kernal headers have anything to do with my wireless network cards drivers failing to load?

The newer kernels (2.6.24-16 and onward) uses the iwlwifi module/driver instead. It also has other dependencies. 

If you are using that kernel and headers, I'm quite certain you will have issues with using the ipw driver. How to solve it, I don't have a clue about.

---

