---
title: "Removed ATI card and replace w/ Nvidia woes..."
date: 2004-11-18
forum: Hardware &amp; Laptops
---

### Post by syNapse on 2004-11-18
I had an ati radeon 9200 that I pulled to relplace with an older geforce tnt2 ultra 32mb card.(I need to sell the radeon).

The problem being that I can no longer boot into the gdm.

I ran apt-get install nvidia-glx and still no dice.

What do I need to do to re-configure??

Thanks...

---

### Post by HungSquirrel on 2004-11-18
I did the same thing (except I replaced a 9800 with a 5700LE).

Sounds to me like you didn't update your XF86Config-4 to reflect the change.

Assuming you have a close-to-default Ubuntu XF86Config-4, you should just need to replace the Driver "fglrx" entry with Driver "nvidia".  If, however, you used fglrxconfig to generate a new XF86Config-4, there will be a lot of non-standard entries in the config file, and I don't know how well the Nvidia card will play with them.

Good luck.

---

