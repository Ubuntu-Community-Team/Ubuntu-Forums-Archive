---
title: "Docking Station - no  video??"
date: 2009-07-12
forum: Hardware
---

### Post by Diamond.Dave on 2009-07-12
Hi, I have a Dell Latitude D820 with 9.04 on it. Runs great in laptop mode. I recently acquired a docking station. I plug in and then turn on. I can watch the boot sequence - right up until the username screen comes up - I don't see it and the monitor goes to powersave mode...any ideas or thoughts would be apprecaited!

---

### Post by Bluefist on 2009-07-15
I have the exact same problem with my Dell Latitude D531 with a radeon x1270 video card running 9.04 when I installed radeon drivers/radeon tool through the package manager.

I did note however that while the DVI port in inactive from the login screen onwards the VGA port on the dock was active, which may be worth trying if your monitor supports VGA. Unfortunately for myself I get a terrible picture (tearing) through VGA at the native resolution (1600 x 1200) of my LCD on my dock.

It has been very frustrating as the open source drivers the ubuntu sets up on install while not quite compatable (a small amount of snow on startup is all I have seen the the video card driver gets initialized) will display through the dock at a max resolution of 1074 x 768.

I'm a new ubuntu user jumping from XP so I'm not the best with the terminal*, but is there a way to force the resolutions modes in Jaunty or force external to DVI? The only info I have seen is to edit older Xorg.config setups that are not current with Jaunty.
[I]
*Most problems have not been to much trouble[/I]

---

### Post by Bluefist on 2009-09-02
Just wanted to update this for prosperity, I solved the video issue when docked by reverting back to 8.04 and installing the propriety ATI fglrx driver (which is not compatible with 9.04 as current).

---

