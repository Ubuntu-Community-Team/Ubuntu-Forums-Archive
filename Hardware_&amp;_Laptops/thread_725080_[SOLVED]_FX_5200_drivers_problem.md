---
title: "[SOLVED] FX 5200 drivers problem"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by FunkyJack on 2008-03-15
I have GeForce FX 5200.
When I install drivers form nvidia website [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)
my gnome doesn't work.
While ubuntu is booting it turns off monitor before login screen.
I'm trying to fix this very long but can't find the solution.
Drivers worked fine on feisty but on gutsy and hardy alpha i'm having this problem.
Anyone have some ideas?

---

### Post by taurus on 2008-03-15
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```
Now, Ubuntu should reboot normally so login with your username and password.  Then, look in System -> Administration -> Restricted Drivers Manager and see if you nvidia card is on the list.  If it is, enable it from there.

---

### Post by FunkyJack on 2008-03-15
I already tried that.
After I install restricted drivers same problem occurs when i restart.

---

### Post by FunkyJack on 2008-03-16
Drivers misspelled one word while creating new xorg.conf.
They wrote 
Defaultdepth    24
instead of
DefaultDepth    24
That damn letter cost me a lot of time :lolflag:

---

