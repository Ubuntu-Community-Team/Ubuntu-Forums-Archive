---
title: "Webcam malfunctioning"
date: 2022-07-25
forum: Hardware
---

### Post by OiPenguin on 2022-07-25
I've got a new *Lenovo IdeaPad 5 Pro 14ACN6* with *AMD® Ryzen 7 5800u with radeon graphics × 16*, running Ubuntu 22.04 with the 5.15.0-41-generic kernel. Everything appears to work great except the integrated webcam. When testing with Cheese I only get poor quality black and white image. When trying to record video it creates a 2 min 18 sec non-working video file in an instant which is not playable. Is there anything I can do to resolve this issue? 

```
$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD RENOIR (LLVM 13.0.1, DRM 3.42, 5.15.0-41-generic) (0x1638)
    Version: 22.0.1
    Accelerated: yes
    Video memory: 2048MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 451 MB, largest block: 451 MB
    VBO free aux. memory - total: 2939 MB, largest block: 2939 MB
    Texture free memory - total: 451 MB, largest block: 451 MB
    Texture free aux. memory - total: 2939 MB, largest block: 2939 MB
    Renderbuffer free memory - total: 451 MB, largest block: 451 MB
    Renderbuffer free aux. memory - total: 2939 MB, largest block: 2939 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 2048 MB
    Total available memory: 5120 MB
    Currently available dedicated video memory: 451 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD RENOIR (LLVM 13.0.1, DRM 3.42, 5.15.0-41-generic)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 22.0.1
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 22.0.1
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.0.1
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

```
$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Cezanne
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: /dev/fb0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=2880,1800
       resources: irq:53 memory:b0000000-bfffffff memory:c0000000-c01fffff ioport:1000(size=256) memory:c0700000-c077ffff memory:c0000-dffff
```

---

### Post by &amp;KyT$0P# on 2022-07-27
Does this webcam work as you would expect in other programs, e.g. guvcview or VLC media player?

---

### Post by SeijiSensei on 2022-07-27
If you have Windows on the machine, does it work with that?

Please open a terminal and type the command **lsusb**. You should see a line like this with information about your camera.

```
Bus 001 Device 003: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
```

Once you know what model it is, we can search to see if it needs a special driver.

The information you gave us above concerns the display, not the camera. I think it's the latter.

---

### Post by OiPenguin on 2022-07-28
> **SeijiSensei said:**
> If you have Windows on the machine, does it work with that?

Please open a terminal and type the command **lsusb**. You should see a line like this with information about your camera.


I've not got Windows installed. Here's the output of **lsusb**.
```
Bus 001 Device 002: ID 13d3:56fb IMC Networks Integrated Camera
```

---

### Post by OiPenguin on 2022-07-28
Streaming with vlc appears to be somehow working. At first attempt it didn't really work, however I decided to start via vlc via terminal to get an output and then it suddenly worked and gave me this output:
```
$ vlc
VLC media player 3.0.16 Vetinari (revision 3.0.13-8-g41878ff4f2)
[00005604989b9640] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
[0000560498a595b0] main playlist: playlist is empty
[00007fe2240042b0] gl gl: Initialized libplacebo v4.192.1 (API v192)
^CQObject::~QObject: Timers cannot be stopped from another thread
```

Gugview also works, both image capture and video capture, however with some errors in the output. This is the terminal output of the video capture:
[https://pastebin.ubuntu.com/p/VBmG7Bcf4f/](https://pastebin.ubuntu.com/p/VBmG7Bcf4f/)

---

### Post by SeijiSensei on 2022-07-28
Searching Google for "IMC Networks Integrated Camera linux" brings up a lot of pages. Maybe there is some useful information there.

---

