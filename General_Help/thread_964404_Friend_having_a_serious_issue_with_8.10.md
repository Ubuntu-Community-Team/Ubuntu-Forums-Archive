---
title: "Friend having a serious issue with 8.10"
date: 2008-10-30
forum: General Help
---

### Post by johnnyxxxcakes on 2008-10-30
So my friend and I just updated to Ubuntu 8.10 this evening, and my update went successful, while his, on the other hand, did not. He said after the downloading of the new packages process completed, it installed them all, and he followed the same procedures as I did.

As instructed, the final step is to restart the system in order to complete the update process; I did that, and it worked, he did that, and it fails to boot. He tells me the computer freezes at the login screen, so he hard resets the computer, and tries again, but it persists.

His computer is a Dell Dimension, I believe, with 2 GB DDR RAM and a 1.8GHz Intel Pentium 4 processor. Any ideas on what we should do to resolve this?

---

### Post by Pro-reason on 2008-10-30
It's probably a video driver issue.  Go to tty1 and run &#8220;sudo envyng -t&#8221;.

(You may have to install the program first, with &#8220;sudo apt-get install envyng-gtk envyng-core&#8221;.)

If that's too technical, then a clean re-installation of Ubuntu Intrepid from the Live CD is probably the best option.  Many people are having problems with updating to Intrepid from within Hardy.

---

### Post by johnnyxxxcakes on 2008-11-01
> **Pro-reason said:**
> It's probably a video driver issue.  Go to tty1 and run “sudo envyng -t”.

If that's too technical, then a clean re-installation of Ubuntu Intrepid from the Live CD is probably the best option.

Okay thanks, we'll have to try that out.

---

