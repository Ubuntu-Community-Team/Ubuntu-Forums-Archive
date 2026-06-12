---
title: "Random Keyboard Error"
date: 2010-01-19
forum: Hardware
---

### Post by winding.roadie on 2010-01-19
Hey everyone,

I seem to be having a rather random keyboard error, and I'm trying to track down the source.  Right now, the keyboard is working fine, and I have no trouble typing messages such as this.  However, in a few minutes, the spacebar, enter, and backspace keys will stop working.  It appears to be only these keys, all other keys maintain functionality.

I'm running a Lenovo 3000 N100 Laptop, with keyboard configuration currently set to generic Intel 105 key US.  I've tried a few other configurations to see if that solves the problem, but to no avail.

Any ideas on what to try here, short of getting a USB keyboard?

---

### Post by winding.roadie on 2010-01-19
Well, I tried ```
sudo dpkg-reconfigure xserver-xorg
```, but that didn't help at all.  I've also tried rebooting, which at first didn't help at all, and then helped a bit when I changed keyboard at the boot screen to "USA-Intl" instead of just regular USA. Key functionality has been flickering in and out for this message, and I'm having to resort to Ctrl-V'ing the spaces in to make it readable. Does anybody have any ideas? At this point, I might just bite the bullet and get a USB keyboard.

---

