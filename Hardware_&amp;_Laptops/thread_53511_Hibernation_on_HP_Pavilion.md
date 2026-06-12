---
title: "Hibernation on HP Pavilion"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-08-01
I have a HP Pavilion zv5474EA.  Clicking hibernate from the logout menu seems to work and the laptop shuts down.

But when powering back on, the kernel crashes and I have to power-cycle to get it to boot again.

Does anyone has this working?

---

### Post by netsyd on 2005-08-01
I gave up on the hibernate functionality (or lack of) and setup suspend2. Its a bunch of work, but in my case it was well worth it. 

[www.suspend2.com](www.suspend2.com)

---

### Post by bgalan on 2006-01-13
same here; i have a pavilion ze4145 and i patched the kernel with suspend2; i just followed the howto; it was a bunch of work, but well worth it.  now i'm struggling with my ati video card. hibernation works very well (and faster than in windows) but i lost my screen outside of x (does that make any sense?). once in gnome, if i press alt+f1 or f2, etc., i cannot see anything but a bunch of colors. i'll keep searching the forums, but if anyone has any ideas, they're welcome! thanks

benjamin

---

### Post by Adrian on 2006-01-13
[QUOTE=nocturn]I have a HP Pavilion zv5474EA.  Clicking hibernate from the logout menu seems to work and the laptop shuts down.

But when powering back on, the kernel crashes and I have to power-cycle to get it to boot again.

Does anyone has this working?[/QUOTE]

Hibernating from the logout menu didn't work for me either, even though my computer didn't crash (it just didn't restore my old session). However, doing this from the terminal worked:
```
sudo -s
echo -n "disk" > /sys/power/state

```

Edit: I have a Compaq Armada 110

---

