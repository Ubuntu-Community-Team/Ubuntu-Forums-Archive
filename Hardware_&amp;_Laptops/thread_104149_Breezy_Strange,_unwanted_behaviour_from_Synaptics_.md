---
title: "Breezy: Strange, unwanted behaviour from Synaptics touchpad"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by riverfr0zen on 2005-12-15
I'm running Breezy, and while the touchpad functions fairly well, there are a couple of weird behaviours that I would like to get rid of.

1) Scroller/mousewheel area registers 'tap-clicks'. I want tap-clicks, but I don't want them to register on the mousewheel area, as it messes the scrolling action up.

2) 'Top' area of the scroller/mousewheel seems to perform 'paste' clipboard operations when it is tapped. I'm really not sure what's going on here, but yep, that's what it does. Really annoying when you're coding - you accidentally paste stuff all over that you shouldn't be.

Output of cat /proc/bus/input/devices is:
I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
H: Handlers=mouse0 ts0 event1
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003


Would appreciate any tips. I tried configuring via qsynaptics, but it doesn't seem to have any settings related to these.  Thanks.

---

### Post by gyrev on 2005-12-15
Hi

On my laptop, the touchpad is really huge, so many times, I had the same issue, taking the cursor anywhere except where it should go!

I didn't find anything in the touchpad configuration, BUT, what I found really convenient, is a plugin for gkrellm called gksyn. there is an Auto mode, that disable the touchpad when you type, and you can configure the timeout lenght. 

[http://gkrellm.net](http://gkrellm.net) for more info, and a link to various plugins. of course, this is ok for Gnome, but there might something like this for kde...


edit: gksyn uses syndaemon, which is part of the synaptics drivers (found in synaptic). it's easy to launch```
syndaemon -d
``` at the session startup

---

