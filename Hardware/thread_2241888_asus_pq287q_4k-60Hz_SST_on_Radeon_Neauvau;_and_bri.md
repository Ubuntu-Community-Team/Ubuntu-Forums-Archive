---
title: "asus pq287q 4k-60Hz SST on Radeon Neauvau; and brief monitor review"
date: 2014-08-29
forum: Hardware
---

### Post by ivo-welch on 2014-08-29
this is to confirm that the ubuntu 14.04 standard radeon driver can drive the asus pq287q monitor in 4k-60hz:

lspci: 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]

make sure to switch the monitor to DP 1.2, as it ships with DP 1.1 by default.  this means going into the monitor menu.

the asus identifies as a

Automatic metadata add icc-2f6d56774b3d0f1fb3088bf97677fd7a to xrandr-Ancor Communications Inc-ASUS PB287Q-66485

it comes up just fine in 4K-60Hz-SST without any tinkering.  however, it is not 100% stable.   this was worse with the fglrx driver, which came up, which did all sorts of crazy things.  the open AMD graphics driver is more stable.  so far, it has woken up correctly from sleep mode three times, but then required a complete cable disconnect, reboot, and cable reconnect to get video back.

It works just fine in multi-monitor configuration next to a Dell 30" 2560x1600 monitor.  the only problem is that the dpi seems wrong, because dragging windows from one monitor to the other reduces the size of the window.

because I have both the 30" IPS monitor and the 28" TN monitors next to one another, I can compare them.  I don't know which I prefer overall.  the asus is much cheaper (and includes built-in speakers).  it has a nice USB 3 hub.  its format is more wide---more like a wide 27" monitor.  both monitors are quite good, but they have very different strengths and weaknesses.  the asus clearly has much higher resolution.  the quality of drawn fonts is more like a Macbook Pro 15" than like an Macbook Air.  however, the asus clearly also has color shifts.  this manifests itself in the following way: it looks like leakage from a monitor backlight (or a background wallpaper that is lighter) at the top, bottom, or both, depending on what height the monitor is.  it does not affect the pleasing quality of black letters on white background.  but it clearly is "off."  if you look for this, you will be annoyed.  if you ignore it, it's great.  I think for reading pdf documents, I prefer the Asus.  for other work, I prefer the Dell.  the best is indeed to have both monitors, except that the window and font sizes change when one drags windows from one to the other.

/iaw

---

