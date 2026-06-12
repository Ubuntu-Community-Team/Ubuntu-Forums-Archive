---
title: "Vulkan not working on Kbuntu 17.10 with Nvidia GeForce GT 705"
date: 2017-11-27
forum: Hardware
---

### Post by yaronct on 2017-11-27
Hi,

I've installed the nvidia driver 384.90 through "Software & Updates  ->  Additional Drivers".

I've tried to run several of the vulkan samples [here](https://github.com/SaschaWillems/Vulkan) and I always get:

[FONT=Courier New]Could not create Vulkan instance : 
ERROR_EXTENSION_NOT_PRESENT[/FONT]

I've tried on several desktop environments and get the same error.

Any idea?

---

### Post by Yellow Pasque on 2017-11-27
Maybe you're experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384/+bug/1726809](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384/+bug/1726809)
It looks like the fix is still in proposed repo.

---

### Post by yaronct on 2017-11-28
It seems not to be yet in the proposed repos for 17.10.

So I'll just wait for now, I guess.

Thanks!

---

