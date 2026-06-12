---
title: "Error activating XKB configuration"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by claudiodallo on 2007-03-22
hi guys, when i start ubuntu a error always start

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

i include 

The result of xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""

 The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

 layouts = []
 model = pc105
 overrideSettings = true
 options = []

i can't set my real keyboard layout ( italian 105), infact i can't use many characters
i try to reconfigure x server, the autodetect input driver detected italian keyboard 105 button it is not the truth couse in system--> .....-> keyboard are selected the once USA layout and i cant add other laytout, 

excuseme for my english but in ubuntu forum italy ,people can't help me

thanks
claudio

:lolflag:

---

### Post by mirceade on 2008-02-04
Related to this: [http://ubuntuforums.org/showthread.php?t=73636](http://ubuntuforums.org/showthread.php?t=73636). And this: [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188)

---

### Post by loveunit on 2008-05-27
moved to [active forum]("http://ubuntuforums.org/showthread.php?p=5056079") - I hope!

---

