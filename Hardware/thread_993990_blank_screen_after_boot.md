---
title: "blank screen after boot"
date: 2008-11-26
forum: Hardware
---

### Post by josephst18 on 2008-11-26
I am trying to install xubuntu on an older machine with an 800 MHz processor and 256 MB of RAM (some of that is shared with the graphics card). I would like to use Wubi to do this, but it tells me I only have 255 MB of RAM. I ignore this, and have continued on to install Xubuntu and reboot. I select Xubuntu from the boot menu, and just follow the normal installation order. The blue bar will go back and forth, and that start to go from left to right, filling up. Once it is about 3/4 of the way, the LCD screen will flicker and go black. The back light is still on, but there is nothing on the screen. When it flickers, it looks like an antenna TV with bad reception, or an old VCR tape. The Xubuntu logo with the loading bars beneath it flicker like I said. There are also green bars that come on screen before the screen goes black, and than it turns unresponsive. When I press the power switch again, the Xubuntu logo re-appears, and the blue bar slowly goes away again, than the system turns off. The computer I am trying to put it on is an old ACER C100 hybrid tablet.

---

### Post by Catalyst2Death on 2008-11-26
Hello,

Have you tried booting into the live CD?  It sounds like the X11 server isn't starting correctly (I could be wrong).  Anyway, when you boot, is there an option for recovery mode?  If there is, that will give you a low graphics terminal, and options to try to recover X11 settings.  If you try to do that automatically, it may fix everything.  If this still doesn't work, you might try switching the video driver to vesa in xorg.conf.  Unfortunately they've changed the format of xorg.conf since gutsy, and I don't know where you need to edit the video driver information.

---

