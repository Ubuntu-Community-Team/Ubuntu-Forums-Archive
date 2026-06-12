---
title: "Latest updates = no wireless LED???"
date: 2008-08-01
forum: Hardware
---

### Post by mariner09 on 2008-08-01
I applied all the kernel updates last week and notice that the wireless LED is now not working.  It was working with previous backports releases.  Anyone know what happened?

I have all the 2.6.24-20 packages for the kernel including backports and ubuntu-modules.  Do I need to go back to compat-wireless?

This is the iwl4965 chipset...

---

### Post by jtniehof on 2008-08-01
I noticed the same thing when I upgraded from gutsy to hardy. Intel 3945ABG controller. I believe there was a switch away from the proprietary driver at that point...I was using the restricted driver in 7.10 (ipw3945, IIRC) and there's no restricted driver even listed in 8.04 (using iwl3945).

---

### Post by mariner09 on 2008-08-01
So, I tried compat-wireless with the 2.6.24-20 kernel and any attempts to unload the std iwl4965 results in a hung machine with flashing caps-lock.

I've reverted back to 2.6.24-19 and the LED works just fine...

Maybe I should disable the bleeding edge repo I've been getting some of these updates from...

---

### Post by charles.figura on 2008-08-01
> **mariner09 said:**
> So, I tried compat-wireless with the 2.6.24-20 kernel and any attempts to unload the std iwl4965 results in a hung machine with flashing caps-lock.

I've reverted back to 2.6.24-19 and the LED works just fine...

I've got the 3945 chipset, and my LED also stopped working under the 2.6.24-20 kernel, where it worked on the -19 release.  The wireless still works, but the upgrade to -20 killed the LED.

---

