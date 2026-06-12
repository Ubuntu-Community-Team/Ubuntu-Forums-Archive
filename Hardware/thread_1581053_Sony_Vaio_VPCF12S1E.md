---
title: "Sony Vaio VPCF12S1E"
date: 2010-09-24
forum: Hardware
---

### Post by plitter on 2010-09-24
Hello,

I have 2 issues that I have found so far with installing Ubuntu 10.04 on this laptop.

    * Touchpad
    * Mic

The touchpad didn't work in the beginning, but i edited  GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp&#8221;, and then it worked, but it doesn't  have multitouch... 

I ran lsinput and found that the 2 likely candidates for the touchpad is  ImPS/2 Generic Wheel Mouse or Macintosh mouse button emulation, but I  am fairly certain that I have Alps Touchpad.
I removed i8042.nopnp from /etc/default/grub and then ImPS/2 Generic Wheel Mouse disappeared.

The mic simply won't work, have tried all of the settings, changing all the alsamixer settings to full.

---

