---
title: "nouveau 3D support for Quadro 600"
date: 2013-01-16
forum: Hardware
---

### Post by Lupius on 2013-01-16
So my coworker and I both have workstations running Quadro 600 on 12.04. We both use the nouveau driver, but he gets to use whatever desktop he wants, and I'm stuck with either Unity 2D or Gnome-fallback.

My .xsession-errors:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
gnome-session-is-accelerated: No hardware 3D support.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session[4787]: WARNING: Session 'gnome-classic' runnable check failed: Exited with code 1
```

And there's no way I'm installing nvidia drivers because there's a bug involving redraw screens that makes terminal unusable. I really want to figure out why I can't get 3D support on my computer. Can anyone help?

---

### Post by Lupius on 2013-01-22
And this is the error message I get when trying to log into Unity and get booted to Unity 2D:
```
Session 'ubuntu' runnable check failed: Exited with code 5
```

---

### Post by Lupius on 2013-02-14
I carefully combed through my Xorg.0.log and noticed that it was trying to load remnants of the nvidia driver at /usr/lib/x86_64-linux-gnu/xorg/extra-modules before loading nouveau. I deleted those and everything works now!

---

