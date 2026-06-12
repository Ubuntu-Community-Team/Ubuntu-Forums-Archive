---
title: "Broadcom Wi-Fi and Natty"
date: 2011-08-20
forum: Hardware
---

### Post by fredsea on 2011-08-20
In a way I solved the problem at hand, but not in the way I hoped. I have been running Lucid on a Lenovo Ideapad for a while (after all, it is LTS :)), and decided to update to Natty, as part of my plan to keep all my computers on the same distribution. Unfortunately the Ideapd uses a Broadcom BCM 4312 Wi-Fi chip, and the open source Broadcom driver does on work with it. Fortunately, the closed STA driver does, so that's how I managed to work with my laptop.

Moving to Natty, none of the drivers worked any more. In general, wireless was recorded as not active, or, when activated, the device was not ready, or it was hardware blocked. The physical switch had no effect, and the only other tool I vaguely know about locking is rfkill, but that did not seem to have any effect either.

What solved the problem was to reinstall Lucid. As soon as I did, the proprietary driver was effective again. Now, I know that this issue is beyond Canonical's reach, as the driver is closed source by Broadcom (but hadn't they open-sourced their drivers lately?? Did I misunderstand the news?). It does seem like something was changed in Natty (or maybe already in Maverick -- I did not upgrade to that) that broke the STA driver. I wonder if there is nothing else I could have done. I can live with this "solution", but I really would rather keep all my machines on the same page.

---

### Post by sbraz on 2011-08-20
i ran into similar problems while testing kernel 3.0. the solution for this issue i ran into is to manually download the driver from broadcom, apply a small patch which i got somewhere i don't remember, compile it, copy the resulting module in place, load the module. done. :)

---

### Post by fredsea on 2011-09-07
Broadcom has a small patch posted for newer kernels - that didn't seem to work either in my case, but, then, my kernel is still from the 2.6.x era.

---

