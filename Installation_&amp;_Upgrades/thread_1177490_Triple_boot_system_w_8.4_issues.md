---
title: "Triple boot system w/ 8.4 issues"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by Hucifer on 2009-06-03
I am installing Ubuntu 8.4 on a box that already has XP and Vista on it. I have gone through the install process twice. I get the login screen, it accepts my credentials, and then I am presented with a blank screen. 

At this point, I am unable to get any response from the system. All I can do is load the disk, and try again. I'm installing on a Dell Optiplex G260.

Any ideas folks?

Thanks,
         Hucifer

---

### Post by dstew on 2009-06-03
Probably this is because the kernel module (driver) that runs the display is having trouble with your hardware. It may be the wrong one, or mis-configrued. You can try to fix it by booting in recovery mode (a grub menu item) which should get you a command line interface. Then enter the command **xfix**. After that, resume normal boot. If you get a graphical interface, go to the System --> Administration --> Hardware Drivers menu and see if you can load a third-party driver for your graphics adapter.

---

