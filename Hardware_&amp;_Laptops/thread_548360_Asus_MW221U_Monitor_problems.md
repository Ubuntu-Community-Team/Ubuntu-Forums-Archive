---
title: "Asus MW221U Monitor problems"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by malayka on 2007-09-11
Hi,

I have just bought bought a new 22 inch Asus MW221U monitor for my Dell SX270 PC, but am unable to get the full 1680 x 1050 screen resolution.

When I use the screen resolution option it doesn't show this option at all.
Is there a way to resolve this problem on Ubuntu 6.06? 

I'm new to this operating system so have no idea where to start. I tried looking for drivers but there don't seem to be any available.

The graphics card is an Intel Graphics Extreme video card.

Any help would be greatly appreciated.

Regards

Chris Gonzalez

---

### Post by malayka on 2007-09-12
for information,

This post relating to the same issue on a Samsung 226BW has resolved the issue on my Asus MW221U.

Awesome!

jpross81  
First Cup of Ubuntu
   Join Date: Jun 2007
Beans: 5 

 
Re: Samsung 226BW widescreen... 

--------------------------------------------------------------------------------

I have been searching all over the net and found this command...


Code:
sudo aptitude install xserver-xorg-video-intelthis enables 1680x1050, 1280x1024, 1280x960, 1152x864, 1024x768, 832x624, 800x600, and 1680x1680 resolutions for my setup. However, when I apply one of the widesreen resolutions such as 1680x1050 the text that does show is not blurry but, the edges of the screen "run off the monitor" as if it is being displayed, but the monitor screen size is too small

---

