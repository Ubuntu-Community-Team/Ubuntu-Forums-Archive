---
title: "Thinkpad only enters C3 power state on console not Xorg!?"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Jingo on 2007-10-29
Hi,

I been toying around with powertop to improve power consumption and battery time on my Thinkpad T42.

What I wonder is why it never enters C3 power state while in Xorg, while having 94% C2 state?
If I switch to tty1 (CTRL-ALT-F1), I get ~15% C3 !

Maybe this can be blamed on the radeon driver (Radeon 7500 card), but what should I do?

I also found futex_wait for both firefox and java producing lots of wake-ups, but thats another story.

/Jingo

---

### Post by Jingo on 2007-11-22
Update:

I tried disabling DRI... now it enters C3 about 20 %

But no 3d then !! :(

---

