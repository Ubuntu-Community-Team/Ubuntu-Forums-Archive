---
title: "Random Shutdowns"
date: 2011-08-10
forum: Hardware
---

### Post by _AltF4_ on 2011-08-10
I am currently running 11.04 on my laptop. Whenever I unplug my laptop, it declares that my battery is critically low and must therefore hibernate. It then promptly hibernates. If I boot/wake my laptop unplugged it will realize that my battery is at 100% and I will have no problems (until I plug it in again).

This is clearly a bug and if know real solution can be found I was wondering if some one could tell me how to make my laptop take no action when battery is critical.

I am using GNOME Power Manager.

---

### Post by Avoozl on 2011-08-10
I know when you open the power management in Lucid, it only offers the options to suspend, hibernate, or shutdown, however there are more options that you can set if you use gconf-editor.

Do alt-f2 and run gconf-editor and then navigate to apps, gnome-power-manager, actions.  Then you will see the option for critical battery and it tells you the options you can manually type in (one of which is "nothing").

---

### Post by _AltF4_ on 2011-08-11
Thanks if I can't find a real solution to the bug I will definitely implement the work around of do nothing on critical

---

