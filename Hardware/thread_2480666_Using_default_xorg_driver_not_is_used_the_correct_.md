---
title: "Using default xorg driver not is used the correct OpenGL version"
date: 2022-11-06
forum: Hardware
---

### Post by aug7744 on 2022-11-06
Hello.

The video is an IGP Radeon HD 3000 using the Kernel driver installed and Mesa updated.
The problem is Radeon HD 3000 hardware compatible is OpenGL 3.3 and using the command below is listed using OpenGL 3.0.
That IGP is before of 2010. Only trying understand if is or not an issue not using OpenGL 3.3.


glxinfo | grep "OpenGL version"
OpenGL version string: 3.0 Mesa 22.2.2 - kisak-mesa PPA

Thus I had downloaded the an driver from
[https://www.amd.com/en/support/graphics/integrated-motherboard-graphics/ati-radeon-3xxx-series/ati-radeon-3000](https://www.amd.com/en/support/graphics/integrated-motherboard-graphics/ati-radeon-3xxx-series/ati-radeon-3000)
but when trying install is showed errors with messages related as if not is possible read Kernel version.
 Possibly not is compatible with kernel above 5.0 ?

What is the better driver to use ? The default kernel driver or try install the driver from AMD ?
How allow use OpenGL 3.3 ? If is possible as fix it ?

Thanks for your reply.

---

### Post by Yellow Pasque on 2022-11-06
The best driver to use is already installed in the kernel. You should have OpenGL 3.3  core profile. You've probably grepped the wrong information and got the compatibility context version (yes, it's confusing).

Please give the output of:
```
glxinfo -B
```

---

### Post by aug7744 on 2022-11-06
Thanks for replying.
Even configuring for IGP memory to 512 MB is the same result. Thus I had selected 64 MB.

glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: AMD RS780 (DRM 2.50.0 / 6.0.6-060006-generic, LLVM 14.0.6) (0x9616)
    Version: 22.2.2
    Accelerated: yes
    Video memory: 64MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 63 MB, largest block: 63 MB
    VBO free aux. memory - total: 509 MB, largest block: 509 MB
    Texture free memory - total: 63 MB, largest block: 63 MB
    Texture free aux. memory - total: 509 MB, largest block: 509 MB
    Renderbuffer free memory - total: 63 MB, largest block: 63 MB
    Renderbuffer free aux. memory - total: 509 MB, largest block: 509 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 64 MB
    Total available memory: 573 MB
    Currently available dedicated video memory: 63 MB
OpenGL vendor string: X.Org
OpenGL renderer string: AMD RS780 (DRM 2.50.0 / 6.0.6-060006-generic, LLVM 14.0.6)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 22.2.2 - kisak-mesa PPA
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.0 Mesa 22.2.2 - kisak-mesa PPA
OpenGL shading language version string: 1.30
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.0 Mesa 22.2.2 - kisak-mesa PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

---

### Post by Yellow Pasque on 2022-11-07
> OpenGL core profile version string: 3.3 (Core Profile) Mesa 22.2.2 - kisak-mesa PPA

You have OpenGL 3.3. The 3.0 compatibility profile is for older programs that need some OpenGL 2.x features.

---

### Post by aug7744 on 2022-11-27
I not have any old software.
Thus I had edited /etc/environment
MESA_GL_VERSION_OVERRIDE=3.3
MESA_GLSL_VERSION_OVERRIDE=330

Now is being used OpenGL 3.3
However I had done another change
MESA_GL_VERSION_OVERRIDE=4.3
MESA_GLSL_VERSION_OVERRIDE=430

Now OpenGL 4.4 works not crashing any software.
I not understand if does any problems in hardware.

---

### Post by #&amp;thj^% on 2022-11-27
> **aug7744 said:**
> 
Thus I had edited /etc/environment
MESA_GL_VERSION_OVERRIDE=3.3
MESA_GLSL_VERSION_OVERRIDE=330

A big heads up those settings are meant for developers and can lead to severe instabilities.
Remove those lines from /etc/environment.

Only use it for applications that won't work without them (and don't be surprised if those applications have all kinds of mysterious problems) .

---

### Post by aug7744 on 2022-11-27
Hello.
All good with you ?

If you say to remove only about avoid softwares crashes in moment not any issues, but is possible some softwares crashing because the settings.

---

### Post by #&amp;thj^% on 2022-11-27
> **aug7744 said:**
> Hello.
All good with you ?.
Yes Thanks.
> **aug7744 said:**
> 

If you say to remove only about avoid softwares crashes in moment not any issues, but is possible some softwares crashing because the settings.

It might be safer to run only per application, as below
You should be able to force the OpenGL version string to 3.3 using the following prefix prior to the command used to launch your software/game/application:
```

MESA_GL_VERSION_OVERRIDE=3.3 <your-application-here>
```

---

### Post by aug7744 on 2022-11-28
@1fallen

Here in Ubuntu Forums you are very well known by their good actions =)

Today appeared the first software having issues with the settings used.
PaleMoon not render the window. Need removing the environment settings.

MESA_GL_VERSION_OVERRIDE=3.3 <your-application-here>

<your-application-here> = software name used when running or the path/software.

Is possible use the settings below ?
MESA_GL_VERSION_OVERRIDE=3.3
MESA_GLSL_VERSION_OVERRIDE=330
MESA_GL_VERSION_OVERRIDE=4.3 /opt/software/x.appimage

When using appimages need add also the appimage name extension ?
The IGP is OpenGL 3.3. However Mesa default settings use 3.0.
I not understand what is the because of limiting to 3.0.
Thus I had forced to 3.3.

Hey you understand because when using radeon driver is loaded both radeon and amdgpu modules ?
Strange loading amdgpu module. That behavior is enabled for default.

---

### Post by #&amp;thj^% on 2022-11-28
I might not completely understand your post, and I'm sorry for that, but to confirm what I've suggested here I'll use: (This is a flatpak)
```
me on Mon Nov 28 at 10:58 AM in ~ branch: (HEAD) 
>> MESA_GL_VERSION_OVERRIDE=3.3 flatpak run com.github.micahflee.torbrowser-launcher
Tor Browser Launcher
By Micah Lee, licensed under MIT
version 0.3.5
https://github.com/micahflee/torbrowser-launcher
Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launching Tor Browser.
Running /home/me/.var/app/com.github.micahflee.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser_en-US/start-tor-browser.desktop
Launching './Browser/start-tor-browser --detach'...


```
Appimages are sand-boxed, and bring a lot of differences in how they would work with my suggestion.
Could you give me one of your problem applications you face with Mesa. (From the terminal please)
I have "balenaEtcher-1.9.0-x64.AppImage" but I created an alias for that named "bet"
So I'd run:
```
MESA_GL_VERSION_OVERRIDE=3.3 bet

(balena-etcher.bin:51548): Gtk-WARNING **: 11:09:48.579: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(balena-etcher.bin:51548): Gtk-WARNING **: 11:09:48.589: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(balena-etcher.bin:51548): Gtk-WARNING **: 11:09:48.589: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(balena-etcher.bin:51548): Gtk-WARNING **: 11:09:48.590: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(balena-etcher.bin:51548): Gtk-WARNING **: 11:09:48.590: Theme parsing error: gtk.css:8318:24: negative values are not allowed.
ready-to-show: 1.200s


```
Screenshot shows result as well.

---

### Post by aug7744 on 2022-11-28
The softwares are :
RetroArch-Linux-x86_64.AppImage
dolphi-emu
pcsx2-v1.7.3511-linux-AppImage-64bit-SSE4-Qt.AppImage
rpcs3-v0.0.24-14142-37aefe58_linux64.AppImage

Setting in environment OpenGL 4.3 the softwares above run correctly.
Using OpenGL 3.3 not run even closing the software window.

---

### Post by #&amp;thj^% on 2022-11-28
yep I see your problem, some Appimage don't quite bundle all necessary libs.
1. RetroArch-Linux-x86_64.AppImage is one of those QT, glibs, will be reliant on the system defaults.
Some are built better and feel free to check with them on that: [https://forums.libretro.com/t/appimage-does-not-start-in-version-1-10-1-1-10-2/36992](https://forums.libretro.com/t/appimage-does-not-start-in-version-1-10-1-1-10-2/36992)
I really can't add anymore to this, and you just may have to use your original settings.
That sends shivers down my spine though, try to keep us updated using your first settings in your first post.

---

### Post by aug7744 on 2022-11-28
Thanks for your replies.
Using default settings not is possible run some softwares.
I not see another way than force OpenGL 3.3.
Not any crashes.
Have an nice week.

---

