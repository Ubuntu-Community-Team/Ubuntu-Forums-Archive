---
title: "Screen Resolution in 8.04"
date: 2008-08-09
forum: Hardware
---

### Post by sytaffel on 2008-08-09
I'm using a Sony VGN-B1XP laptop (intel 855 GME integrated graphics) and have just upgraded from 7.10 to 8.04.

when I first installed 7.10 ubuntu recognized the screen fine and defaulted to 1400x1050.

then one day ubuntu stopped recognising things properly and i could only select 640x480 or 800x600

So I decided to update to 8.04 hoping that this would sort things out... Instead I can now only use ubuntu in 640x480, which is basically unusable.

Help... How do I configure ubuntu properly to work with my system.

Thanks

---

### Post by overdrank on 2008-08-09
> **sytaffel said:**
> I'm using a Sony VGN-B1XP laptop (intel 855 GME integrated graphics) and have just upgraded from 7.10 to 8.04.

when I first installed 7.10 ubuntu recognized the screen fine and defaulted to 1400x1050.

then one day ubuntu stopped recognising things properly and i could only select 640x480 or 800x600

So I decided to update to 8.04 hoping that this would sort things out... Instead I can now only use ubuntu in 640x480, which is basically unusable.

Help... How do I configure ubuntu properly to work with my system.

Thanks

Hi and welcome. Have you tried to boot into recovery mode and use the xfix option? this may solve your issue. If not you can try and use the command ```
gksu displayconfig-gtk
``` and to move the window use the alt key and single click and hold with the mouse and move the window to click the apply button.

---

### Post by sytaffel on 2008-08-09
Awesome... Thank you... Xfix sorted things out for me.

Thank you for sharing your knowledge and expertise

Sy

---

### Post by phidia on 2008-08-09
> **overdrank said:**
> Hi and welcome. Have you tried to boot into recovery mode and use the xfix option? this may solve your issue. If not you can try and use the command ```
gksu displayconfig-gtk
``` and to move the window use the alt key and single click and hold with the mouse and move the window to click the apply button.

Is xfix and gksu displayconfig-gtk a replacement for sudo dpkg-reconfigure -phigh xserver-xorg?

---

### Post by overdrank on 2008-08-09
> **phidia said:**
> Is xfix and gksu displayconfig-gtk a replacement for sudo dpkg-reconfigure -phigh xserver-xorg?

Well that is hard to say. It is a added tool for me as it works for some and not for others. :)
As I still use the sudo dpkg-reconfigure -phigh xserver-xorg from time to time.

---

