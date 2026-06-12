---
title: "feisty fglrx display corruption (fix)"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by spookware on 2007-04-21
Ran in to a bug while beta testing feisty a while back. Reverted to dapper. Loaded up feisty final only to discover that the issue is still there.

The problem. ATI x1650 running on a SIS chipset. System boots up and properly displays gdm screen. However after logon the dsiplay is oddly currpted. certain widgets do not render properly. scrolling just totally messes things up. Even the simple splash screen that appears before the gnome desktop is odd as the background image is transparent.

If used for more than a minute or so like this the system hard locks and must be reset (key combos are of no use).

I posted a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108402](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108402)

solution is to turn on composite. I know it sounds backwords but it works. the fglrx module will figre out that composite is on and disable DRI as a result. This kills 3D or course but 2D will work fine.

hope this helps anyone that might run in to the same issue.

---

### Post by deaderthanyou on 2007-04-21
Just out of curiosity, what is displayed when you type ```
glxinfo | grep direct
``` into a console?

---

