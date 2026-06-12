---
title: "[SOLVED] Keyboar layout keeps resetting to US"
date: 2008-08-23
forum: General Help
---

### Post by barkerben on 2008-08-23
Hi - I am running Ubuntu 8.04 with a Microsoft Desktop Elite bluetooth keyboard - this works fine (I am using it now)

However, every time I reboot the PC, my default layout resets to US. When I go to Preferences --> Keyboard --> Layout, the only option is United Kingdom (I deleted US), but the only way to get my layout back is to select another keyboard, then reselect my own...

Any ideas how I can fix this?

Cheers,

Ben

---

### Post by eggdeng on 2008-08-23
Try
```
gksu gedit /etc/X11/xorg.conf
```
Look for the line
```
Option "XkbLayout" "xx"
```
where xx is uk, us or whatever. Edit this value, save the file, log out and back in again.

---

### Post by prshah on 2008-08-23
> **barkerben said:**
> but the only way to get my layout back is to select another keyboard, then reselect my own...


Add "setxkbmap" to your startup sessions. For more details, see:
[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040) and [[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567)

---

### Post by barkerben on 2008-08-23
Ah - that first suggestion did it - just read the links from the second poster, ad have now added setxkbmap to my startup, so it should work if I need to change it in the future via the GUI. Thanks all :-)

---

