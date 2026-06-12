---
title: "X - Blank screen on gdm start"
date: 2011-07-11
forum: Hardware
---

### Post by d7415 on 2011-07-11
Quick summary:

Hardware: Intel integrated Graphics (unused) and nVidia GT520M

[LIST=1]
[*]New laptop. Installed Natty, seemed ok.
[*]Noticed Compiz wasn't working, installed NVidia proprietary driver.
[/LIST]

Here I've lost track. I think it complained that I hadn't run nvidia-xconfig, and *that* caused the restart-into-blank-screen. Here's what I've tried:

[LIST]
[*]No xorg.conf = boots fine, with EDID, using intel (as far as i can tell), but no compiz/effects.
[*]If I don't specify the BusID in xorg.conf it gets confused. In this case, I think it won't even respond to ctrl-alt-F1 to open a tty.
[*]When it sees the NVidia card, it can't see the (laptop) monitor through EDID.
[*]Tried modelines and the disable-EDID options I could find. Result: mdoes not validated, blank screen.
[*]Added a CustomEDID file, boots into a blank screen with no obvious error messages. This is the file I've included.
[/LIST]

That doesn't feel complete, but it's all I can think of right now.

Any suggestions welcome!

[Edit to add: I found it odd that there don't seem to be any real errors/warnings any more but it still won't work]

---

### Post by d7415 on 2011-07-13
**Update:**

Followed the advice below from [theiszm.wordpress.com]("https://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/").

```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```

This means I only have the Intel graphics (and not my paid-more-for Nvidia graphics) running, but I do at least get Compiz...

It's a start, and it's usable.

---

