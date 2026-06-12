---
title: "hw_random fails on boot -- how do I blacklist?"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2007-01-21
Since usplash quit working for the moment after I upgraded to Edgy, I now get to see all the lovely boot messages (not a whole lot, actually).  One of them is that hw_random tries to load, but can't start the RNG, so it fails.

While it doesn't seem to actually hurt anything, I figured I might as well blacklist the module, so I added "hw_random" to a file named /etc/hotplug/blacklist (I had to create the blacklist file).  However, when I start up I still get the error.  I saw somewhere that somebody suggested created a hotplug.d directory with a file inside it containing the module name to blacklist, but that didn't work either.

What's the right way to do this?

---

### Post by lswb on 2007-01-21
Look for /etc/modprobe.d/blackist and add the module there instead. Hotplug was used with earlier distros.

---

### Post by Kensey on 2007-01-23
Thanks!  That did the trick.

---

### Post by M0nk3yM4n on 2007-01-24
In the /etc/modprobe.d/blacklist file I put in

> blacklist hw_random

This is correct yes? Still getting startup errors.

---

