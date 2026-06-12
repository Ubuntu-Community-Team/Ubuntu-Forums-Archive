---
title: "Is dual monitors possible with this setup?"
date: 2008-12-21
forum: Hardware
---

### Post by cb951303 on 2008-12-21
I looked through many dual monitors threads but I'm confused about the necessary setup to make it possible.

I have a [128MB Winfast Leadtek 6600GT TDH]("http://www.leadtek.com/eng/3d_graphic/overview.asp?lineid=1&pronameid=147") graphics card which runs flawlessly on Ubuntu 8.10 with latest beta NVIDIA drivers (180.16).

I also have two 17" identical LCDs.

What exactly do I need (hardware? software? some kind of cable?) to run them in dual mode meaning I will be able to drag windows from one monitor to another.

Thanks

---

### Post by trapgate on 2008-12-21
Should be pretty simple: plug one monitor into the DVI port, the other into the VGA port, and then use nvidia's setup tool (it's on the applications/system tools menu) to set up TwinView mode, and extend the desktop onto the second monitor.

---

### Post by cb951303 on 2008-12-21
> **trapgate said:**
> Should be pretty simple: plug one monitor into the DVI port, the other into the VGA port, and then use nvidia's setup tool (it's on the applications/system tools menu) to set up TwinView mode, and extend the desktop onto the second monitor.

Unfotunately my monitors doesn't work with DVI. I tried with a DVI-to-ANALOG converter but it didn't work.

So I'm guessing a "Y analog monitor" cable should be fine? Something like this? [IMG]http://snpi.dell.com/sna/images/products/large/CN_I177155.JPG[/IMG]

---

### Post by trapgate on 2008-12-21
No, that won't work. It'd give you the same image on both monitors. Usually hooking a VGA monitor up to a DVI port is just a matter of a simple adapter, since most DVI connectors include a set of analog pins (they're the pins around the funny bladed connector to one side of the plug.) Some DVI connectors don't have those pins though, and maybe that's the case with your adapter. In that case you'd need a real digital-to-analog signal converter, which would probably cost about the same as a new monitor.

---

### Post by cb951303 on 2008-12-22
I tried again with the adapter and this time it worked. The first time I tried I didn't reboot the system apperently DVI needs a restart to work :) Also 2 monitors works now, I didn't even bother with config files. It worked out of the box.

Another question about dual monitors: When I run a fullscreen application it always uses both monitors and centers the image (half of the image is in 1 monitor and half in other one)
Is there fix for this? I would like to play a fullscreen game while browsing web in other one...


Thanks

---

