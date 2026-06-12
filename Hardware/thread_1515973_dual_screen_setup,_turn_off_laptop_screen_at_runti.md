---
title: "dual screen setup, turn off laptop screen at runtime"
date: 2010-06-23
forum: Hardware
---

### Post by flocki on 2010-06-23
Hi!

Since my Laptop screen is broken and keeps flickering **all the time**, I have been using my TFT again and covered the laptop screen. Problem is that this way I can't use the built in camera. I'm having an nvidia card and have set the screens to clone. With nvidia-settings I can perfectly turn off the LCD at runtime. But is there a commandline program I can run to turn off just the laptop-screen?

I have been playing with ```
xset -display :1.0 dpms force off
``` but it turns off both screens.

I don't want to disable the screen in the xorg.conf, since the external Monitor is on the blink and sometimes gives me "Resolution not supported" errors, even if nothing has changed.

I would appreciate any held.

---

