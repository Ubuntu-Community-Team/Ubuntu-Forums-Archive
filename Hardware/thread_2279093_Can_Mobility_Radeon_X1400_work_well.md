---
title: "Can Mobility Radeon X1400 work well?"
date: 2015-05-20
forum: Hardware
---

### Post by dreamlayers on 2015-05-20
Recently I tried to install Ubuntu 15.04 on my Dell Inspiron 6400 laptop, with ATI Mobility Radeon X1400. The proprietary fglrx driver doesn't support the GPU because it is too old. The open source radeon driver mostly works but has graphical glitches and uses too much power. It's bad enough that it makes me avoid running Linux there.

The radeon.dpm kernel parameter does not enable any power management, because it's for newer GPUs. Switching power profiles via /sys/class/drm/card0/device/power_profile does decrease power consumption, but causes the kernel to complain about a PCI error NMI and seems to cause worse graphical corruption. It also decreases performance by an unacceptable amount, far more than I'd expect just based on GPU clock speed changes.

It's interesting how in Windows, GPU temperature varies depending on GPU load, and in Linux it seems to mainly depend on the power profile. It's as if Linux fails to properly idle the GPU when unused. It's not really overheating, but choosing between wasting energy and bad performance is not acceptable for battery use.

I know X1400 is slow, but it's perfectly fine for desktop use in Windows 7 and for Google Earth. I'm not into gaming, so I don't care about much else. I don't have corruption problems in Windows even if running more intense 3D software.

---

### Post by mörgæs on 2015-05-21
How does it work if you add XFCE og LXDE as the desktop environment?

---

### Post by Yellow Pasque on 2015-05-21
In theory, the X1400 should work well enough for basic desktop usage. It's not going to give you any video decoding help, so video playback will likely be a sore spot (I'm guessing you have a Turion and they struggle on their own from other user reports I've seen.) It seems you already found this page and I'm guessing you tried the dynpm profile (is that what gives the PCI error)?: [http://wiki.x.org/wiki/RadeonFeature/#index3h2](http://wiki.x.org/wiki/RadeonFeature/#index3h2)

If running a lighter desktop as mörgæs suggested doesn't help, I don't think there's much you can do short of filing bug reports on freedesktop. Ubuntu 15.04 has a pretty recent kernel and I don't see anything in the changelogs of the 4.x kernels that would make me recommend trying the latest upstream kernel (though radeon devs may suugest it if you file a bug report).

---

### Post by dreamlayers on 2016-03-14
I gave up on using Linux on my laptop because of this video corruption. The exact same corruption is still present in Ubuntu 16.04. It starts as soon as the boot switches from standard PC text mode to a high resolution text mode and is also present in X in SDDM and Cinnamon. GPU temperature seems lower in 16.04, as if the GPU is being idled properly.

Things have gotten worse in other ways. In Chrome I needed to disable GPU rasterization to display web pages, and the address bar in Firefox has inverted colours.

This thread seems to be about the video corruption bug: [https://lists.launchpad.net/ubuntu-x-swat/msg52452.html](https://lists.launchpad.net/ubuntu-x-swat/msg52452.html)

I have the high resolution 1680x1050 display.

I was thinking this was a video mode issue because the flickery corruption never persisted. After "xrandr --output LVDS --mode 1400x1050" the corruption went away, but of course then I'm not in native resolution anymore. Then doing "xrandr --output LVDS --mode 1680x1050" got me back to native resolution without corruption.

---

### Post by mörgæs on 2016-03-15
> **dreamlayers said:**
> 
I was thinking this was a video mode issue because the flickery corruption never persisted. After "xrandr --output LVDS --mode 1400x1050" the corruption went away, but of course then I'm not in native resolution anymore. Then doing "xrandr --output LVDS --mode 1680x1050" got me back to native resolution without corruption.

Good, then please mark the thread 'solved'.

---

### Post by him610 on 2016-03-15
There maybe another way to solve the problem. Caution: it may or not work for you.
In the file, /etc/default/grub
There is a line, #GRUB_GFXMODE=640x480
Uncomment the line (remove the crunch), and change it to read ,  GFXMODE=1680x1050
Save the file, then from the CLI run update-grub
Reboot your machine

This method worked for me when experiencing corrupted video and screen tears on an integrated AMD APU/GPU. Maybe it will work for you.

---

