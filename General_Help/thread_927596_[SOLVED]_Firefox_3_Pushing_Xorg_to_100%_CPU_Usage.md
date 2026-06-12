---
title: "[SOLVED] Firefox 3 Pushing Xorg to 100% CPU Usage"
date: 2008-09-23
forum: General Help
---

### Post by quoick on 2008-09-23
I have found firefox to be fairly sluggish ever since I upgraded to Hardy and have been keeping an eye on the resource usage using htop. After a short time Firefox and Xorg (with Xorg being the greatest amount) will take up the majority of the CPU cycles and often sit at 100%. I am writing this using Opera and the combined usage is <8%. Is this a known issue and if so is there a work around?

I have seen a couple of threads similar to this but they have blamed Hardy (recommending a reinstall of Gutsy) or the drivers for a 8600GT (which I also have) but the new drivers haven't improved anything.

---

### Post by ianhaycox on 2008-09-23
If you have Desktop Effects enabled try turning them off. I.e. Set Visual Effects in the Appearances Preferences dialogue to None.

---

### Post by quoick on 2008-09-23
> **ianhaycox said:**
> If you have Desktop Effects enabled try turning them off. I.e. Set Visual Effects in the Appearances Preferences dialogue to None.

A good point - thanks. Unfortunately it doesn't affect the problem.

---

### Post by quoick on 2008-09-23
I have recently re-installed Hardy because of the problem from a new downloaded image and it still exists. Also I tried removing all the addons to see if this would help but alas, no.

---

### Post by blierp on 2008-09-24
i'm experiencing the same problem but it only started a few days ago. Perhaps it has something to do with a recent update? Maybe unrelated but firefox hangs a few times per day as well. After being unresponsive for 20~ seconds it becomes usable again.

---

### Post by quoick on 2008-09-24
I disabled all of my addons and re-enabled them one by one then rebooted Firefox. It turns out it was caused by RSS Ticker. Shame, cause I loved that thing.

---

