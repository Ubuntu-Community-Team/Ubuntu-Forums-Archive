---
title: "Computer doesn't react to keyboard/mouse input after screen is locked and goes blank"
date: 2014-06-20
forum: Hardware
---

### Post by amborsdorfer on 2014-06-20
After locking the screen using Ctrl+Alt+L or Super+L, and waiting until the screen goes blank, my computer doesn't react to keyboard input or mouse movements anymore (not even Caps Lock or changing to TTY1), and I can't wake it up to log in. This also happens when the PC was in suspend, resumed, and then the screen went blank after a minute or two. This does **not** happen, when I leave my (logged in) PC unattended and wait for it to lock automatically!

It is a pretty annoying issue, because I have to plug the PC out to be able to use it again.

It's Ubuntu 14.04 on a DELL Optiplex GX620 (tower PC).
The PC has been running Arch Linux and Debian Sid before without any problems. Thus I conclude that the issue must be with LightLocker, but I am not sure.

---

### Post by amborsdorfer on 2014-06-20
Edit: I just checked, light-locker is **not** installed! That is weird, I thought that it is default in 14.04. This is how my lockscreen looks like:

[IMG]http://ubuntuportal.com/wp-content/uploads/2014/03/ubuntu-14.04-Lock-Screen.png[/IMG]

It's gnome-screensaver I think. I replaced it with light-locker and the issue seems gone.

---

