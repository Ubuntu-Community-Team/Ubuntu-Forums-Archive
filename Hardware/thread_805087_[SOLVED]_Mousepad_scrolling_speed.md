---
title: "[SOLVED] Mousepad scrolling speed"
date: 2008-05-23
forum: Hardware
---

### Post by syrrus21 on 2008-05-23
I have a Dell Inspiron E1505 laptop. It has mousepad which has the side-scroll feature. Ever since I upgraded to Ubuntu 8.04, the scroll speed has changed and it scrolls really fast. I tried the System > Preferences > Mouse method, but there was no option on scrolling speed. I'm fairly new to Ubuntu, so I did not want to mess with the configuration file on my own. Any help would be appreciated.

---

### Post by Zorael on 2008-05-23
This is with a Synaptics touchpad, I assume? I think you can configure this in [FONT="Courier New"]gsynaptics[/FONT]. It's in the universe repositories; find and tag it for installation in Synaptic.

You'll need to add a line to your /etc/X11/xorg.conf file to get it to work, but that's not hard to do.
```
*<run box (Alt+F2)>*
gksu gedit /etc/X11/xorg.conf
```
```
*<somewhere in the InputDevice section for Synaptics Touchpad>*
Option		"SHMConfig" "on"
```
Save your work, log out, restart X with Ctrl+Alt+Backspace, log in, start the gsynaptics app and see if it works.

---

