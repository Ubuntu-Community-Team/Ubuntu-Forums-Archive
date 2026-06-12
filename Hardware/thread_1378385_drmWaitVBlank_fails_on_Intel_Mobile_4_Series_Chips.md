---
title: "drmWaitVBlank fails on Intel Mobile 4 Series Chipset"
date: 2010-01-11
forum: Hardware
---

### Post by mprada on 2010-01-11
Hi,

I'm trying to run, Gazebo, a robot simulator which, amongst other things, should display a 3D scene of what's going on. When I run it, the program seems to run (I mean, the window stays open and the program doesn't crash), but the 3D scene part of the UI is totally blank. The program outputs this:

```
[...]
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
[...]
```

I've been trying to find some answer to this issue, and I've found loads of stuff, but none of it seems to solve the problem for me. I tried forcing the 'intel' driver on /etc/X11/xorg.conf; changing the 'Synchronization with vertical refresh' parameter using 'driconf'; and some other stuff as well.

My laptop is a Dell Latitude E5400, and carries an 'Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller' (as stated by lspci).

Oh, and I'm running Ubuntu Karmic.

Any suggestion about what to try?

Thanks!

---

### Post by xt8088 on 2010-01-18
I'm getting the same thing when launching freeorion.

I've tried the following....

vblank_mode=3 ./freeorion-start

If tried what I believe are all the possible options for the vblank_mode (0-3), and I still get a blank window for a few seconds then nothing...

---

### Post by ljrossi on 2010-01-25
[http://intellinuxgraphics.org/2009Q4.html]("http://intellinuxgraphics.org/2009Q4.html")

There talks about a patch , i dont know how to use it.

 Is another game but same trouble

---

### Post by rafa.lopez on 2010-06-11
Hi all,
I am experiencing the same problem here with Gazebo.

Where any of you able to solve the problem with the Mobile 4 Series Chipset?

---

