---
title: "New Intel i810 makes X crashes upon resize"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Svip on 2007-06-04
I was informed that a new driver for the Intel graphics cards were in the repo; "xserver-xorg-video-intel".

I downloaded it, and to my pleasure, my widescreen laptop is actually widescreen now, compared to the 4:3 resolution I used before.  But to my utter dismay, whenever an application wants to resize the resolution (e.g. fullscreen or similar) X crashes. :(

Any concepts?  And if you need any more information, just call.

---

### Post by ramjet_1953 on 2007-06-04
Yes, I found the same problem.

I just removed the new driver, re-installed the old i810 driver and configured my laptop widescreen with 915resolution.

It works fine under Feisty and allows software to control resolution, without X crashing.

Regards,
Roger :cool:

---

### Post by crimsun on 2007-06-05
> **ramjet_1953 said:**
> It works fine under Feisty and allows software to control resolution, without X crashing.

Feisty's -intel is not the final version but an RC snap.

---

### Post by Svip on 2007-06-05
> **ramjet_1953 said:**
> Yes, I found the same problem.

I just removed the new driver, re-installed the old i810 driver and configured my laptop widescreen with 915resolution.

It works fine under Feisty and allows software to control resolution, without X crashing.

Regards,
Roger :cool:

Can you tell me how?  I never got the i915resolution program to work.

---

