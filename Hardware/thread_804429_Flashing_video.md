---
title: "Flashing video"
date: 2008-05-23
forum: Hardware
---

### Post by PauGNU on 2008-05-23
Hi

As of I installed the new ati driver (catalyst 8.5), when I play some movie pictures start to "flash" (on vlc, totem...).

I know I can solve this problem going back to the old driver, but there is a problem: even with the old driver it happened the same when I used Zatoo: video screen started flashing. However, playing movies was right. 

If I disable compiz, all works fine. But I can't understand why when I install the new version all video turns out flashing. Has somebody the same problem?

---

### Post by benevolent on 2008-05-23
Question: How did you install the new driver??? With EnvyNG??

Thanks,
dimitris

---

### Post by PauGNU on 2008-05-23
Hi

I installed the new driver manually: creating and installing deb files. I dindn't modify any xorg.conf line.

---

### Post by Kemono on 2008-05-23
Have you tried to set the output module (**Preferences>Video>Output Modules->-Check the "Advanced Options" box**) to X11 in VLC?

---

### Post by PauGNU on 2008-05-24
Thanks!! It worked!

But, do you know how can I configure the output video mode on Zatoo? (it still flash and there is no "preferences"...)

---

### Post by Kemono on 2008-05-24
I'm sorry but I'm not familiar with Zattoo. I guess it will only work properly if you turn off compiz.

I have an ATI card and when the screensaver kicks in it starts flashing. ATI cards are not all that well supported in GNU/Linux.

---

