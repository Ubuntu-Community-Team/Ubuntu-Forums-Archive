---
title: "errors with ATI 5750 in dmesg hal_evergreen.c"
date: 2010-10-13
forum: Hardware
---

### Post by shukle on 2010-10-13
Hi!

I am getting the following message in dmesg several times (>10) each day:
```
 Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line: 64
```

Other than that everything seems to work fine. Any ideas what causes this? I am using 10.10.

I am using the proprietary driver:  
8.723.1-100408a-098580C-ATI

---

### Post by Alfagulf on 2010-11-24
Hi,
I am getting exactly the same error in dmesg!!

Did you have any luck finding out what is going on?

Thanks

---

### Post by davidjmemmett on 2011-04-13
I get this in 11.04 (beta), every time I see it, something *around* X has given up, if I switch to any of the TTYs (Ctrl+Alt+[1-6]) and then back to 7, I find that the cursor is movable but I have a black screen with white dashes along the bottom.

I've raised a bug[0] for this.

[0] - [https://bugs.launchpad.net/ubuntu/+bug/760159](https://bugs.launchpad.net/ubuntu/+bug/760159)

---

