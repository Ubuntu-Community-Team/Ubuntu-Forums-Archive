---
title: "External Monitor Woes"
date: 2011-01-20
forum: Hardware
---

### Post by siwelchungster on 2011-01-20
This is my issue:

I'm trying to connect a Acer X233h monitor to my laptop's VGA port (only option). My laptop employs Intel 4500MHD Intel Integrated Graphics.

Ubuntu detects the native resolution fine: 1920x1080 @ 60hz (EDIT, monitor specs says it actually supports 1920x1080 @ 75hz), but when I try to set the external monitor resolution to that, I get the following output:

[IMG]http://i56.tinypic.com/4ilyz4.jpg[/IMG]

This renders it completely unusable.

I noticed that the monitor recognizes the input it's getting as 1680x1050 through the acer monitor settings.

The catch is that if I set the resolution to anything lower, like 1440 x 900, then it works fine, albeit a bit stretched out.

BTW: I've tried Ubuntu/Kubuntu 10.04, 10.10 and same issue. I am also using xorg-edgers.

---

### Post by siwelchungster on 2011-01-29
some more information after more testing:

It seems that i'm able to add a 1680x1050 mode via xrandr and set the display to that. however i want 1920x1080, which is still producing the same distorted output.

it seems that I get the distortion all throughout the boot, in console, and in gdm.

---

### Post by siwelchungster on 2011-02-04
more info:

I just tried installing the latest lucid kernel: 2.6.32-25-generic on my maverick installation.

and the external monitor works perfectly.

what could have changed between this and say, 2.6.35?

---

### Post by siwelchungster on 2011-03-15
UPDATE: I've made the upgrade to natty alpha 3, with kernel version 2.6.38-6-generic. Still have the same issue that's been appearing since the Maverick kernels.

Lucid/Lucid Kernels seemed fine after clean install...

---

