---
title: "How to switch off laptop screen"
date: 2010-07-28
forum: Hardware
---

### Post by Mortesins93 on 2010-07-28
Hello,
I have an ASUS A4GA laptop with a screen that doesn't work (it just stays white), so I connected a monitor to it and it works fine. I just wanted to know if there was a way of turning off the laptop screen?
Thanks in advance

---

### Post by Mortesins93 on 2010-11-08
Anyone? I can't accept the fact that I can only do it on Windows.

---

### Post by efflandt on 2010-11-08
Details depend upon which video chip you have and whether you are using default video drivers or proprietary drivers.  If you are using default drivers, see what **xrandr** command shows for your video devices.  Then you can use **xrandr** to turn off the laptop display (see **man xrandr**).

For example on my laptop with Intel video it would be:

```
xrandr --output LVDS1 --off
```But your laptop display may be something other than LVDS1 (possibly a DFP device if nvidia).

If you are using proprietary video drivers, the app for that (NVIDIA X Server Settings or whatever ATI uses for Catalyst) should be able to switch to your external display as primary and disable your laptop display.  But it may be difficult to do that with nvidia because it might not default to mirroring like ATI and Intel seem to do.

---

### Post by Mortesins93 on 2010-11-12
Thanks sooooo much. This little trick of yours solved [my video problems]("http://ubuntuforums.org/showthread.php?t=1558497&page=1") too. I am not a 100 percent sure but after switching the screen on I could finally watch videos on VLC. So do I have to save the settings or something or not?
Thanks again.

---

