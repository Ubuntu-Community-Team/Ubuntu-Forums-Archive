---
title: "DVD/CD writing problems after installation VMware"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Julianz on 2008-03-04
I hope somebody can help me with this.
After I installed (and later uninstalled) vmware on Ubuntu 7.10 Gutsy I cannot write any CD or DVD's with any burning software. I tried it with about five of the most common burning software. I can read from the drives (I have on CD and one DVD burner)
I put the drives for testing in another PC's (with Ubuntu gutsy) and they work fine. Somehow something is blocking write access in my configuration I guess. I tried to burn logged in as other users but no luck.

Somebody an idea?
Many thanks,

---

### Post by wednesday allfather on 2008-03-04
Is VMWare running while you are trying to burn from Ubuntu?

If XP has control of your drive (dev/scd0) or whatever yours are called, perhaps another program can not access it

Try changing the virtual machine's settings to not alow it to use either drive.  If that works, then you know XP just wasn't willing to share.

---

