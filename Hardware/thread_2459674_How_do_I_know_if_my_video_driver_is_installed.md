---
title: "How do I know if my video driver is installed?"
date: 2021-03-23
forum: Hardware
---

### Post by pretty_pink_petunia on 2021-03-23
Well, I recently installed Lubuntu 18.04 for my old Asus eee 1001pxd laptop and for now it has worked great but I have a question, does it have the video driver by default? when I see the screen settings I get "Intel powered classmate" but I have an intel gma 3150 and that is why I open this thread.

my laptop specs:

Intel atom n455 2 threads 1.66Ghz - 1.67Ghz
2GB RAM
Intel Graphics Media Accelerator 3150 - 64mb




excuse my bad english, i'm latin american.

---

### Post by Yellow Pasque on 2021-03-23
> does it have the video driver by default?

Yes. To check, look at:
```
glxinfo -B
```

---

### Post by pretty_pink_petunia on 2021-03-23
I entered the command in the terminal and it appears this:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Pineview M x86/MMX/SSE2 (0xa011)
    Version: 20.0.8
    Accelerated: yes
    Video memory: 384MB
    Unified memory: yes
    Preferred profile: compat (0x2)
    Max core profile version: 0.0
    Max compat profile version: 1.4
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 2.0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Pineview M x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 20.0.8

OpenGL ES profile version string: OpenGL ES 2.0 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
```


Does it mean that everything is correct?

---

### Post by Yellow Pasque on 2021-03-23
Yes, everything is good there.

---

### Post by pretty_pink_petunia on 2021-03-23
Thank you very much for the help. :)

---

### Post by Yellow Pasque on 2021-03-23
You are welcome. Please mark the thread SOLVED by using the Thread tools menu above the first post.

---

