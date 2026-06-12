---
title: "Type transparency problem."
date: 2008-09-29
forum: General Help
---

### Post by sototallycarl on 2008-09-29
From day one with Ubuntu, I have noticed a blocky appearance to transparent type (see attached). It happens for emerald window decorations, awn bubbles, firefox and countless others when type alpha tweens or is on a semi transparent background. It happens with compiz on and off.

I have a feeling this is not an unsolvable issue as many screen shots show perfectly clear transparent type, yet have no found any notes on the topic.

Setup: Hardy, 24" iMac, ATI 2600HD via fglrx

---

### Post by sototallycarl on 2008-10-05
Found the issue, finally. Subpixel Order in Font Rendering Details was set to VRGB. Change it to any other setting and the type renders perfectly. Bug? Or is this the intended outcome?

---

