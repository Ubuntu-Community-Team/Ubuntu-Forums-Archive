---
title: "Multiple GPUs, headless, mangled X11"
date: 2024-03-19
forum: Hardware
---

### Post by ilithium on 2024-03-19
Hi all

I'm dropping a post here as I'm not sure where else to ask and I think a forum is better than AskUbuntu as I get the feeling my question will spark multiple other questions.

**Context**
I have an Ubuntu Server (22.04 LTS) that runs a bunch of headless applications for me and which I use for browsing via X11-Forwarding over SSH.

When I installed this (a fresh install after update from previous LTS version failed), when I installed Google Chrome (via its PPA) it was responsive and usable - now it's not. It's very, very slow.

When I start Chrome, I get messages talking about issues with display drivers and rendering (see below for log output).

For context, this system has three display drivers:


[LIST]
[*]AMD Radeon (via the CPU/APU)
[*]nvidia RTX 3050
[*]nvidia GeForce GTX 1050 Ti
[/LIST]

To power the nvidia cards, I am using nvidia driver 525.147.05, provided by *ubuntu-drivers*.

These nvidia cards are used by Docker (using the nvidia container toolkit) and this part is all working well.

**The Problem**
When i start Google Chrome over SSH (with X11-Forwarding enabled) I get the following errors:

```

[3006827:3006852:0319/090004.667494:ERROR:object_proxy.cc(576)] Failed to call method: org.freedesktop.DBus.StartServiceByName: object_path= /org/freedesktop/DBus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
No matching fbConfigs or visuals found
failed to load driver: zink
No matching fbConfigs or visuals found
failed to load driver: swrast
[3006873:3006873:0319/090005.932767:ERROR:angle_platform_impl.cc(44)] Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
ERR: Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
[3006873:3006873:0319/090005.932970:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create GL context.
[3006873:3006873:0319/090005.933008:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
[3006873:3006873:0319/090005.980722:ERROR:angle_platform_impl.cc(44)] Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
ERR: Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
[3006873:3006873:0319/090005.981017:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
[3006873:3006873:0319/090005.981126:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[3006873:3006873:0319/090005.981220:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[3006873:3006873:0319/090005.981336:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
[3006873:3006873:0319/090006.474981:ERROR:angle_platform_impl.cc(44)] Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
ERR: Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
[3006873:3006873:0319/090006.475124:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create GL context.
[3006873:3006873:0319/090006.475187:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
[3006873:3006873:0319/090006.518608:ERROR:angle_platform_impl.cc(44)] Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
ERR: Display.cpp:1052 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension

```

[B]What I've tried already
[/B]Reading through these messages, it looked like I didn't have OpenGL installed or available, so I tried to install it via the *freeglut3-dev* package - no change.
I also tried installing *wayland*, *chooswm* and *icewqm* on the basis there may be something wrong with my window manager, but none of these made any difference

[B]The Question I'm Asking
[/B]At this point, I'm basically running out of ideas and would like some help:

a) Understanding these messages
b) A pointer to some documentation around how X11 and OpenGL tie together, so that I could potentially work this out myself

Sorry for the really long post - any help would be greatly appreciated!

FWIW, I've been using Ubuntu for nearly 20 years, both as a workstation and managing clusters of servers (I'm a technical architect) but issues like this aren't generally within my remit.

Thanks!

---

### Post by MAFoElffen on 2024-03-19
Those errors are usually caused by a failed mesa update (zink, swrast)
```

sudo apt install --reinstall mesa-utils

```

---

### Post by ilithium on 2024-03-19
Thanks for the suggestion, @MAFoElffen. 

No dice, I'm afraid. I ran that command, it completed successfully and I'm getting the same errors.

Same thing happens after a reboot.

Any other suggestions?

---

### Post by MAFoElffen on 2024-03-19
X-Forwarding deals with X11, not Wayland. 

Let's debug this a bit... Is that error coming up on the remote server, or the local client?

Wait... I have honestly never tried to run Google Chrome over SSH w/ X-Forwarding. Let me spin up a VM on my server, install Chrome on it, connect via ssh w/ X-Forwarding, and see what mine does... Maybe there is a trick or two to that(?)

BRB

---

### Post by MAFoElffen on 2024-03-19
I ssh'ed w/ X-Forwarding into the vm and started google-chrome-stable:
```

mafoelffen@Mikes-B460M:~$ ssh -X mafoelffen@192.168.122.58 /usr/bin/google-chrome-stable
mafoelffen@192.168.122.58's password: 
failed to create drawable
[3903:3903:0319/172645.449541:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3903:3903:0319/172645.459536:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3903:3903:0319/172645.459600:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
failed to create drawable
[3903:3903:0319/172645.509875:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3903:3903:0319/172645.511780:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3903:3903:0319/172645.511825:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[3903:3903:0319/172645.511899:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[3903:3903:0319/172645.511978:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
failed to create drawable
[3903:3903:0319/172645.597698:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3903:3903:0319/172645.597761:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3903:3903:0319/172645.597789:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
failed to create drawable
[3903:3903:0319/172645.655679:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3903:3903:0319/172645.655734:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3903:3903:0319/172645.655756:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[3903:3903:0319/172645.655792:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[3903:3903:0319/172645.655815:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
[3903:3903:0319/172645.682673:ERROR:viz_main_impl.cc(196)] Exiting GPU process due to errors during initialization
failed to create drawable
[3963:3963:0319/172646.269023:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3963:3963:0319/172646.269219:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3963:3963:0319/172646.269383:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
failed to create drawable
[3963:3963:0319/172646.325170:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3963:3963:0319/172646.325398:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3963:3963:0319/172646.325536:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[3963:3963:0319/172646.325660:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[3963:3963:0319/172646.325712:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
failed to create drawable
[3963:3963:0319/172646.397866:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3963:3963:0319/172646.398101:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3963:3963:0319/172646.398225:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
failed to create drawable
[3963:3963:0319/172646.460651:ERROR:angle_platform_impl.cc(44)] Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
ERR: Display.cpp:1070 (initialize): ANGLE Display::initialize error 12289: Could not create the initialization pbuffer.
[3963:3963:0319/172646.460830:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create the initialization pbuffer.
[3963:3963:0319/172646.461001:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[3963:3963:0319/172646.461166:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[3963:3963:0319/172646.461257:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
[3963:3963:0319/172646.470217:ERROR:viz_main_impl.cc(196)] Exiting GPU process due to errors during initialization
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
/usr/bin/google-chrome-stable

```
It came up and ran fine... But that VM does not have anything special connected to it. That one does not have any GPU pass-through for it = Just vanilla graphics.

That was from my laptop... >> ssh -X into my server >> ssh -X starting chrome... Came up fine through the tunnel from my laptop's desktop.

Note: I am used to seeing those kinds of  error messages while running X-Forwarding, starting app's from the commandline... And ignore them.

---

### Post by MAFoElffen on 2024-03-19
So backing up...

X11 is running on my local (10.0.0.72). My server is headless (10.0.0.3). Here are the displays and seats of the VM (192.168.122.58):
```

SESSION  UID USER       SEAT  TTY 
     11 1000 mafoelffen       
      2 1000 mafoelffen seat0 tty2

2 sessions listed.
mafoelffen@focal-zfs-01:~$ loginctl show-session 2 -p Type
Type=wayland
mafoelffen@focal-zfs-01:~$ loginctl show-session 11 -p Type
Type=tty
mafoelffen@focal-zfs-01:~$ sudo lspci -knnn | grep -A3 -E 'Display|VGA|3D'
00:01.0 VGA compatible controller [0300]: Red Hat, Inc. QXL paravirtual graphic card [1b36:0100] (rev 05)
    Subsystem: Red Hat, Inc. QEMU Virtual Machine [1af4:1100]
    Kernel driver in use: qxl
    Kernel modules: qxl

```
This is how I run things for X-Forwarding... Local device to VM connection.

EDIT:
Actually... I toggled my desktop on my laptop to Wayland, did the same and it came up fine (XWayland).

---

### Post by MAFoElffen on 2024-03-19
My curiosity goes into another line of thought and practice...

My thoughts, backed by years of experience with high-end graphics on Unix and Linux, and additionally with Servers...

NVidia Graphics drivers pole the ports for attached displays to retrieve the EDID from those displays. By default, if a device is not found, it disables those ports and does not load the NVidia drivers... There are ways around that for headless servers.

How do you have this Server configured to get around that?

---

### Post by ilithium on 2024-04-09
Thanks for sharing this. I'd never really looked at this before, so I've executed these commands on my (headless) server:

```
justin@server:~$ loginctl
SESSION UID USER SEAT TTY
2598 1000 justin pts/0
1 sessions listed.

justin@server:~$ loginctl show-session 2598 -p Type
Type=tty
justin@server:~$ sudo lspci -knnn | grep -A3 -E 'Display|VGA|3D'
[sudo] password for justin:
10:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:2507] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:c978]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
--
21:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] [10de:1c82] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GP107 [GeForce GTX 1050 Ti] [1043:862a]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
--
30:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [1002:1638] (rev c9)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [1002:1636]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```

So I can see I'm connected via pts/0 (virtual tty) but I don't know how I'd figure out which display manager my X11 session is using.

---

### Post by ilithium on 2024-04-09
When I saw your post on EDIDs, that rang a bell based on having read something similar elsewhere, @[COLOR=#000000]MAFoElffen.

So I ordered a couple of "HDMI Dummy Plugs" from Amazon ([product link]("https://www.amazon.co.uk/dp/B07C4WD9CH")) and popped these in on the basis that the nvidia drivers probably weren't "activating".

Nothing really has changed, though and I'm still stuck with in the same position, i.e:

```

justin@server:~$ google-chrome-beta
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
[1407597:1407597:0409/132831.992987:ERROR:angle_platform_impl.cc(44)] Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
ERR: Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
[1407597:1407597:0409/132831.993358:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Could not create GL context.
[1407597:1407597:0409/132831.993597:ERROR:gl_display.cc(786)] eglInitialize OpenGL failed with error EGL_NOT_INITIALIZED, trying next display type
[1407597:1407597:0409/132832.039403:ERROR:angle_platform_impl.cc(44)] Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
ERR: Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
[1407597:1407597:0409/132832.039686:ERROR:gl_display.cc(515)] EGL Driver message (Critical) eglInitialize: Cannot create an OpenGL ES platform on GLX without the GLX_ARB_create_context extension.
[1407597:1407597:0409/132832.039815:ERROR:gl_display.cc(786)] eglInitialize OpenGLES failed with error EGL_NOT_INITIALIZED
[1407597:1407597:0409/132832.039877:ERROR:gl_display.cc(820)] Initialization of all EGL display types failed.
[1407597:1407597:0409/132832.039947:ERROR:gl_ozone_egl.cc(26)] GLDisplayEGL::Initialize failed.
[1407597:1407597:0409/132832.514268:ERROR:angle_platform_impl.cc(44)] Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
ERR: Display.cpp:1086 (initialize): ANGLE Display::initialize error 12289: Could not create GL context.
... etc ...

```

Any further thoughts?
[/COLOR]

---

