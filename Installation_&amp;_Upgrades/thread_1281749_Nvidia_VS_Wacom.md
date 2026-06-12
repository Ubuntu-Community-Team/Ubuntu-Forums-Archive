---
title: "Nvidia VS Wacom"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by shnurui on 2009-10-03
Ok, now I've got auto-point and contact sensitivity on my bamboo fun.

I follow all the help files I find, the old install,

When I add the InputDevice section to the Setup portion, it frags my video driver and I have to undo the modifications to the X11/xorg.conf
[https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)

I really need my cursor (mouse egg ball thing) to work.

I've tried doing it with the video card uninstalled, when I reinstall the video card, it removes the input data.


Help.

---

### Post by Favux on 2009-10-03
Hi shnurui,

You have to tell us what version of Ubuntu you are using.  I suspect you are in Jaunty (9.04).  See my reply to your other post.

In Jaunty you no longer use the xorg.conf.  I suspect your problem is adding Wacom entries in xorg.conf and not getting the "ServerLayout" section correct.  If so comment out (#) all your Wacom entries and "ServerLayout" and reboot.  Then look at my reply on the other thread.

---

### Post by shnurui on 2009-10-05
> **Favux said:**
> Hi shnurui,

You have to tell us what version of Ubuntu you are using.  I suspect you are in Jaunty (9.04).  See my reply to your other post.

In Jaunty you no longer use the xorg.conf.  I suspect your problem is adding Wacom entries in xorg.conf and not getting the "ServerLayout" section correct.  If so comment out (#) all your Wacom entries and "ServerLayout" and reboot.  Then look at my reply on the other thread.

I'm just now upgrading to 9.04, hadn't gotten it to work on 8.04, and 8.10, I'll try a 9 install in t - 40min.

I just don't want it to fight my nvidia driver, may have to drop a line to them.

---

