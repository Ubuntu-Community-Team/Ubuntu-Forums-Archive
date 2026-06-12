---
title: "Unable to switch vidoe resolution on 9.10 server"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ayshu on 2009-11-03
Just installed 9.10 server edition and the console now start up in 1920x1200 resolution, so the characters are too small for me.  Added "nomodeset" in grub config file and the resolution drop back to 640x480 after reboot.  How should I change video mode to, say 1280x1024?  915resolution is removed from 9.10 and there is xserver is not part of ubuntu server edition.

Any suggestion?

---

### Post by ayshu on 2009-11-03
I found the solution here, need to blacklist i915 too.

[http://rogst.homeip.net/wiki/index.php/Console,_Enable_framebuffer](http://rogst.homeip.net/wiki/index.php/Console,_Enable_framebuffer)

---

### Post by mamen0330 on 2010-01-25
The link doesn't work. can you send the steps?thank you.:P

---

