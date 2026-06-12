---
title: "Just built a computer, has xubuntu 7.04 on it..."
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Majin Zero on 2007-08-01
And when xwindows starts it locks up.

I can start in recovery mode and it will run a command line fine, but right after running startx, it'll crash.

It also can't even finish a windows install.

What's going wrong here?

---

### Post by merlinus on 2007-08-01
Probably your video card.

You might try this:

At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then reboot.

When up-and-running you can search for the correct drivers for the card.

-merlin

---

