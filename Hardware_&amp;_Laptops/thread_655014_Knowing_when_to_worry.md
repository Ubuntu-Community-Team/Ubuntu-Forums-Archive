---
title: "Knowing when to worry"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Battie on 2007-12-31
One of the toughest things to troubleshoot is an error that cannot be replicated.  On a Windows machine, I usually let it go if it only happens once.

But this is Linux.  A random restart on a lightly loaded system just shouldn't happen.

My temperatures look good, but I'm not sure how to get the voltage readings (lm-sensors doesn't mention them).

Since this only happened once (and maybe one other time a few months ago) should I worry?  What might have caused it, if not hardware?

Thanks!

---

### Post by hardyn on 2007-12-31
Radom restarts are can usuallly be caused by one of three things: unstable power, defective ram, defective motherboard.

It is however totally possible that it was a freak thing and will never happen again.  Im sure it is possible to cause a similar reboot with a software condition, but any time such a reboot has happened to me, it could have been explained through the above 3.

try the memtest86,  inspect the contacts in the power supply, is the power supply making excessive heat?

---

### Post by Battie on 2007-12-31
Thanks.  I'll run Memtest while I'm out tomorrow.  I've never been sure -- how many passes to you usually take before you are satisfied?

---

### Post by eku on 2007-12-31
> **Battie said:**
> Thanks.  I'll run Memtest while I'm out tomorrow.  I've never been sure -- how many passes to you usually take before you are satisfied?

By running every test possible, it shouldn't take more than one time to see if it's good or not.

L

---

### Post by arashiko28 on 2007-12-31
Most important it is a laptop or a desktop? I have a laptop and it forced shut down twice, I was worried like hell until I saw the message on the screen before it shutted down, even if I can't get a temp reading, it was 95% of the maximum and shutted down to protect my processor. I didn't noticed it was that I accidentally covered the vents.

Happy new year!!!

---

### Post by Battie on 2007-12-31
Thanks, both of you.

It's a desktop (homemade).  I had a laptop that did the same thing.  Some old version of the Kubuntu update manager would bug out and consume the CPU the whole time until it overheated.  I never let that process run after I figured it out. O_o

---

### Post by hardyn on 2008-01-01
you don't have stalled CPU fan do you?

---

