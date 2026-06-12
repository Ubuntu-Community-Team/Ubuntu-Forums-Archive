---
title: "[LUBUNTU] Mouse preferences are not applied, slow mouse"
date: 2013-05-23
forum: Hardware
---

### Post by Lucas Malor on 2013-05-23
I can apply settings for mouse only if I:

[LIST=1]
[*]open the settings dialog 
[*]unplug and replug the USB mouse 
[*]change the acceleration setting 
[*]do not close the settings dialog 
[/LIST]

If so, settings are applied. If I close the dialog or I change the Sensitivity setting, preferences get resetted and I must unplug and replug the mouse another one time. I also tried to change /desktop/gnome/peripherals/mouse/motion_acceleration and  motion_threshold manually without success.

I have no problem with mouse on Ubuntu 12.04.

---

### Post by ohnonot on 2013-05-23
try [this]("http://www.mintppc.org/forums/viewtopic.php?p=7404&sid=1d99fc3c149a797a59d46347cd63f181#p7404")!
maybe without the @.
and the autostart file should be in ~/.config/openbox/.
also ```
man xset
```.

---

### Post by Lucas Malor on 2013-05-23
It's a little tricky but it works! The file for Lubuntu is
```
~/.config/lxsession/Lubuntu/autostart
```
Thank you very much!

---

### Post by ohnonot on 2013-05-24
xset is also good for many other things, like ditching your screensaver ;-)

glad to be of help.

...please mark as solved! top right: thread tools.

---

### Post by Lucas Malor on 2013-05-24
Mh, I can't mark it as solved in thread tools, so I changed the prefix... is it normal?

---

