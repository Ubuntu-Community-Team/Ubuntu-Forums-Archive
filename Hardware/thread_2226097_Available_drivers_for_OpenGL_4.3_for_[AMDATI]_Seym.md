---
title: "Available drivers for OpenGL 4.3 for [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]"
date: 2014-05-25
forum: Hardware
---

### Post by mustapha_rashidudd on 2014-05-25
I have a **TOSHIBA SATTELITE R840-12C**
my graphics card: **[AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]**
this is on **Ubuntu 14.04**

I want to program opengl4.3, however I get the when I typed in ```
glxinfo
``` in the terminal

....
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAICOS
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.0
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
V_vdpau_interop, 
    GL_OES_EGL_image, GL_OES_read_format, GL_S3_s3tc
.....
.....
.....
OpenGL version string: 3.0 Mesa 10.1.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trinary_minmax, GL.....
.....
There was a lot of output, so I cut a lot out, the dots represent the stuff before or after the output I wanted to show you.

As you can see, above It says:
```
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.0
``` in the first block
and ```
OpenGL version string: 3.0 Mesa 10.1.0
``` in the second


Now I've also tried installing the propriety drivers, however, it doesn't solve the problem.
I tried the AMD graphics accelerators from fglrx AND
AMD graphics accelerators from fglrx-updates.

So I've set it back to Using X.Org X server -AMD/ATI display driver wrapper from xserver-xorg-video-ati, which is the open source and tested version.

So which drivers would I need, or is this hardware not even supported for opengl in Ubuntu 14.04?

also, the when i set it doesn't run 3.3 code properly, it just opens it with a black screen, only 2.x, 3.0 i think works.

---

