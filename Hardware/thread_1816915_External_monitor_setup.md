---
title: "External monitor setup"
date: 2011-08-02
forum: Hardware
---

### Post by pepribal on 2011-08-02
Hi,

I've got an old laptop, which I'm trying to setup with Ubuntu. The screen is spoiled, but I've connected it to a monitor, and I can work through this monitor. The thing is that I cannot select the proper screen resolution of the monitor: I cannot select the proper one.

I've got Ubuntu 11.04, and the VGA is a SiS M650 / 740.

If I type

```
glxinfo | grep rende
```I get:

```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
```so I assume drivers are OK by default, and OpenGL should be running.

How can I then select the proper monitor resolution, if I really can do it?

Thanks.

---

