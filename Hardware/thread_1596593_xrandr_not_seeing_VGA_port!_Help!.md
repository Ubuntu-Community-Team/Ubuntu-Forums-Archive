---
title: "xrandr not seeing VGA port! Help!"
date: 2010-10-14
forum: Hardware
---

### Post by xorkal1985 on 2010-10-14
Hi there,
  I'm having a problem connection to an external projector using my VGA port on my Laptop. I have a Sony Vaio VPCCW21FX with the Nvidia 310m graphics card. I am also using Ubuntu 10.04.

  I need to connect to a projector via my VGA port on the side of my computer for a speech I'm doing in college about Linux, and I want to show them what it looks like.

  I have the current drivers for my video card installed from nvidia(currently 256.53) and everything looks amazing. I type Xrandr to see my device connections but it only shows my default laptop monitor. And it doesn't say VGA: disconnected like I would expect it to. I also tried plugging in the projector, did xrandr and still, nothing shows up! Noticing a trend? :confused:

  So I do a little research on the net and find everyone is using nvidia-settings to auto-config and mirror their desktop to another screen... I had the pfojector plugged into my VGA port, and went to nvidia-settings, display configuration, and hit detect displays(which I would assume its just doing an xrandr behind the GUI). Nothing at all.

  I tried messing with xorg.conf to get it to show up, anything I could think of, and still nothing.

  Could someone please offer some insight to how I can get this thing working? Thank you!

---

### Post by efflandt on 2010-10-14
I don't think xrandr shows complete or correct information with nvidia drivers.  For example xrandr says my HDTV is connected at 50 Hz, when System > Administration > **NVIDIA X Server Settings** show it is at 60 Hz.  Did you try finding it from NVIDIA X Server Settings.

Nvidia refers to VGA as "CRT" regardless of actual display type.  A digitally connected display (or your laptop display) is "DFP" (as in display flat panel).

You might try booting with the projector already connected and on, or if you connect it and turn it on after you are running, try "logging out" of X and then back in.  I don't have a working laptop with nvidia, but I believe I had to do one of those two things for X to see an external VGA display with ATI or Intel video.

---

### Post by xorkal1985 on 2010-10-14
I will try that, and tinker around... crossing my fingers and hoping this works.

I'll report back with my findings! :)

---

### Post by xorkal1985 on 2010-10-15
So I tried both of those ideas to have it recognize that the vga port is even being used, and still nothing. Is there a way I can Manually configure my vga port to show up? like, how do I find the busID of the port, set up the screen/monitor stuff in xorg.conf? Thanks

---

