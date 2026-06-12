---
title: "[SOLVED] All Memory Not Detected"
date: 2008-10-04
forum: General Help
---

### Post by HOLOGRAPHICpizza on 2008-10-04
I have 512 mb of ram installed on my computer, but only some of it is being detected by linux. This happens in all linux distros.

The stick of RAM says 512 mb.
The BIOS says 510 mb.
Xubuntu says 373.4 mb.
System Rescue CD says 367.4 mb.

What gives?:confused:

---

### Post by Joeb454 on 2008-10-04
Chances are 2mb is being used for Video memory. I experience a similar thing on both all machines I have

---

### Post by HOLOGRAPHICpizza on 2008-10-04
Yeah.... I'm missing a *lot* more than 2 mb...

---

### Post by HOLOGRAPHICpizza on 2008-10-08
Does *anyone* have an idea of where my ~140mb of RAM are disappearing to?

---

### Post by Kevbert on 2008-10-08
Have you run memtest from the grub menu ?  Some of the memory could be shared with the video card. What's the output from ```
free -m
```?

---

### Post by HOLOGRAPHICpizza on 2008-10-08
DOH! Man I feel *stupid*! I can't believe I never thought of the *graphics*! I looked in the BIOS and sure enough, 128MB was being used for integrated graphics! Thanks for the slap in the brain!

And by the way, nice avatar, I got *really* creative on mine. :grin:

---

### Post by Kevbert on 2008-10-08
No problem. I decided to make my own avatar using Inkscape rather than just get one from elsewhere like a lot of the others here.  That way I can make subtle changes to it.

---

