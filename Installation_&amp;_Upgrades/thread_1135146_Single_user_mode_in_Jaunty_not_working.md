---
title: "Single user mode in Jaunty not working?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by juise- on 2009-04-24
Hi,

I was upgrading from 8.04 -> 9.04, and run into a problem where X would get stuck (complaining about missing 'freetype' library, not responding to any kb/mouse input so I cannot get to console or respond to the 'OK' button shown). Something like this was expected, so I tried using 'single' boot parameter at grub to go and edit my xorg.conf.

So far so good, I get a nice debconf menu prompting for options what to do (normal boot, root shell etc). Only that the menu does not work! (trying to navigate with arrow keys just prints ^B etc.)

Any ideas how to skip this and get a root shell?

---

### Post by juise- on 2009-04-29
Ok, I found the problem with single user mode.

It seems that simply adding 'single' to boot options is not enough, I also had to remove 'splash' option. Doing that, the single user 'Recovery menu' works fine.

---

