---
title: "Touchpad and other problems with suspend/hibernate on Fujitsu-Siemens Amilo Pro v2010"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by hastour on 2006-06-05
Ok, after a clean dapper reinstall I'm quite determined to get this working at last. It used to work under Breezy with suspend2, it also did with suse 10.0. Now it's like that:

- With Klaptop both suspend and hibernate seem to work, but after resuming my touchpad is disabled.

- When using KPowersave, suspend brings me up a black screen (but it seems working behind it, I can close the system by blindly pressing keys). And hibernate brings me an interesting pattern of white and black stripes. Both can be helped by swithing to a virtual console and back, and that's the closest thing to "it works!" I achieved. Oh, but after suspend touchpad is still missing.

Any ideas? Making the touchpad work with klaptop would do it for me, I don't really need the fancy new kpowersave...

---

### Post by RetroMan on 2006-07-11
Sorry to resurrect this thread, but I found it via google and thought I might be able to help out a bit.

I had the same problem, although I noticed that if I waited about 10 seconds before using the touchpad, it would work.  I think the problem has disappeared now after I added 'Driver   "synaptics"' to my touchpad section in my xorg.conf (and possibly, a 'Load "synaptics"' in my modules section).  Hope this helps.

---

