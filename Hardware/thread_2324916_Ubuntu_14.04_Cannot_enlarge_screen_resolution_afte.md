---
title: "Ubuntu 14.04: Cannot enlarge screen resolution after Debian dist-upgrade"
date: 2016-05-17
forum: Hardware
---

### Post by nfidia on 2016-05-17
Hi,

I have two Linux installations on my machine:

a) Debian

b) Ubuntu Studio 14.04.4

Some weeks ago I executed a dist-upgrade in my Debian installation, from Debian 7 to Debian 8.

Before the Debian dist-upgrade I had as well as in installation a) and in installation b) each a screen resolution greater than 1024 x 768 pixels.

Having executed the Debian dist-upgrade I had a screen resolution of only 1024 x 768 pixels as well as in installation a) as in installation b).

I successfully could change (enlarge) the screen resolution in installation a) (Debian 8) by adding the following lines in the file /etc/default/grub in installation a):

> GRUB_GFXMODE=1400x1050x32
GRUB_GFXPAYLOAD_LINUX=keep

I then executed update-grub in installation a) (Debian 8).

This resulted in a larger screen resolution in installation a). This is the result of xrandr in installation a):

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1400 x 1050, current 1400 x 1050, maximum 1400 x 1050
default connected primary 1400x1050+0+0 0mm x 0mm
1400x1050      0.00*

So until here everything is fine.

Now the problem:

I have inserted the same lines, i.e 

> GRUB_GFXMODE=1400x1050x32
GRUB_GFXPAYLOAD_LINUX=keep

in the file /etc/default/grub in installation b) (Ubuntu Studio 14.04.4), then executed update-grub, but the screen resolution in installation b) (Ubuntu Studio 14.04.4) is still 1024 x 768 pixels, so the screen resolution did not get larger. And it is not possible to set a higher screen resolution via the desktop manager of Ubuntu Studio (here: XFCE). This is the result of the xrandr command in Ubuntu Studio 14.04.4:

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1024x768       60.0* 
800x600        60.3     56.2  
848x480        60.0  
640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)

How can I enlarge the screen resolution in my Ubuntu Studio 14.04.4 installation?

---

My graphics card is a Radeon HD 4350.

The following graphics card driver is installed in my Debian 8 installation:

xserver-xorg-video-radeon

The following graphics card driver is installed in my Ubuntu Studio 14.04.4 installation:

xserver-xorg-video-radeon

Regards,

nfidia

---

