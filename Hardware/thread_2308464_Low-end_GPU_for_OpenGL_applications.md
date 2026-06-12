---
title: "Low-end GPU for OpenGL applications"
date: 2016-01-03
forum: Hardware
---

### Post by Megadoomer on 2016-01-03
Hello everyone,

years ago, I bought myself a desktop workstation for audio and video work. I now switched from Windows 7 to Ubuntu Studio and I noticed that some programs do not recognise my GPU (Nvidia Quadro 5000): In Kdenlive, the option to enable OpenGL for playback is greyed out and Blender automatically selects my CPU as the rendering device without the option to select the GPU. I am not exactly sure what the cause of this is, as I am using the most recent proprietary Nvidia driver from the official repository (the free driver unfortunately generates flickering) and there are no other signs of malfunction. Maybe it is because of the Version of OpenGL ES that the driver is using or because of some other incompatibility, unfortunately I am not very well versed when it comes to GPUs, so not sure.

Anyhow, I was looking to replace this old card with a newer model in the low-end spectrum (think <200$ range) and I was wondering which one to pick in order to get the best OpenGL performance out of it?

Are AMD cards maybe better for OpenGL than Nvidia?
Do the free Radeon drivers maybe work better than the Nvidia ones? I guess it would be great to use them instead of the proprietary ones.
What series or models tend to work best with Ubuntu (...Studio 15.10, soon 16.04)?
Where is the best place for me to look for benchmarks and experiments? Did someone test various cards specifically in Ubuntu?

I would be glad if someone here, who is a bit more experienced in this topic than me, could give me some hints or share a little knowledge about this. I tried an extensive web search, but unfortunately could not find anything that answers these questions for me.

Kind regards!

---

### Post by Yellow Pasque on 2016-01-04
The Quadro 5000 is not that old (it's basically equivalent to a GTX 465 with much better floating point performance). It supports the latest version of OpenGL (4.5) assuming you have a recent nvidia driver installed. There's no reason you should have to buy a newer card for Blender or Kdenlive.

First thing to do is check driver function:
```
glxinfo | grep -i gl
```

---

