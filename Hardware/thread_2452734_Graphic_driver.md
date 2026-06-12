---
title: "Graphic driver"
date: 2020-10-27
forum: Hardware
---

### Post by d-aka on 2020-10-27
Hi,

I have a quite new asus laptop and I am trying to understand which video driver (package + version) uses this computer. Can please someone help me ? Thanks !

Model : Asus VivioBook X512JA
```

amel@laptopasus:~$ lspci  | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Iris Plus Graphics G7 (rev 07)
```
```

# cat Xorg.1.log | grep -i loadmodule
[   352.287] (II) LoadModule: "glx"
[   352.288] (II) LoadModule: "modesetting"
[   352.288] (II) LoadModule: "fbdev"
[   352.289] (II) LoadModule: "vesa"
[   352.312] (II) LoadModule: "fbdevhw"
[   352.312] (II) LoadModule: "glamoregl"
[   352.421] (II) LoadModule: "fb"
[   352.421] (II) UnloadModule: "fbdev"
[   352.421] (II) UnloadModule: "vesa"
[   352.667] (II) LoadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.279] (II) UnloadModule: "libinput"
[   457.280] (II) UnloadModule: "libinput"

```
```
amel@laptopasus:~$ dpkg -l | grep -i intel
ii  gir1.2-ibus-1.0:amd64                         1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - introspection data
ii  i965-va-driver:amd64                          2.4.0-0ubuntu1                        amd64        VAAPI driver for Intel G45 & HD Graphics family
ii  ibus                                          1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - core
ii  ibus-data                                     1.5.22-2ubuntu2.1                     all          Intelligent Input Bus - data files
ii  ibus-gtk:amd64                                1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - GTK2 support
ii  ibus-gtk3:amd64                               1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - GTK3 support
ii  intel-media-va-driver:amd64                   20.1.1+dfsg1-1                        amd64        VAAPI driver for the Intel GEN8+ Graphics family
ii  intel-microcode                               3.20200609.0ubuntu0.20.04.2           amd64        Processor microcode firmware for Intel CPUs
ii  iucode-tool                                   2.3.1-1                               amd64        Intel processor microcode tool
ii  libdrm-intel1:amd64                           2.4.101-2                             amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libibus-1.0-5:amd64                           1.5.22-2ubuntu2.1                     amd64        Intelligent Input Bus - shared library
ii  libigdgmm11:amd64                             20.1.1+ds1-1                          amd64        Intel Graphics Memory Management Library -- shared library
ii  python3-ibus-1.0                              1.5.22-2ubuntu2.1                     all          Intelligent Input Bus - introspection overrides for Python (Python 3)
ii  xserver-xorg-video-intel                      2:2.99.917+git20200226-1              amd64        X.Org X server -- Intel i8xx, i9xx display driver

amel@laptopasus:~$ dpkg -l | grep -i video
ii  cheese                                        3.34.0-1ubuntu1                       amd64        tool to take pictures and videos from your webcam
ii  cheese-common                                 3.34.0-1ubuntu1                       all          Common files for the Cheese tool to take pictures and videos
ii  gnome-video-effects                           0.5.0-1ubuntu1                        all          Collection of GStreamer effects
ii  libaom0:amd64                                 1.0.0.errata1-3build1                 amd64        AV1 Video Codec Library
ii  libavc1394-0:amd64                            0.5.4-5                               amd64        control IEEE 1394 audio/video devices
ii  libavcodec58:amd64                            7:4.2.4-1ubuntu0.1                    amd64        FFmpeg library with de/encoders for audio/video codecs - runtime files
ii  libcheese-gtk25:amd64                         3.34.0-1ubuntu1                       amd64        tool to take pictures and videos from your webcam - widgets
ii  libcheese8:amd64                              3.34.0-1ubuntu1                       amd64        tool to take pictures and videos from your webcam - base library
ii  libde265-0:amd64                              1.0.4-1build1                         amd64        Open H.265 video codec implementation
ii  libdv4:amd64                                  1.0.0-12                              amd64        software library for DV format digital video (runtime lib)
ii  libgme0:amd64                                 0.6.2-1build1                         amd64        Playback library for video game music files - shared library
ii  libmatroska6v5:amd64                          1.5.2-3build1                         amd64        extensible open standard audio/video container format (shared library)
ii  libmpeg2-4:amd64                              0.5.1-9                               amd64        MPEG1 and MPEG2 video decoder library
ii  libplacebo7:amd64                             1.7.0-2                               amd64        GPU-accelerated video/image rendering primitives (shared library)
ii  libtheora0:amd64                              1.1.1+dfsg.1-15ubuntu2                amd64        Theora Video Compression Codec
ii  libv4l-0:amd64                                1.18.0-2build1                        amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                          1.18.0-2build1                        amd64        Video4linux frame format conversion library
ii  libva-drm2:amd64                              2.7.0-2                               amd64        Video Acceleration (VA) API for Linux -- DRM runtime
ii  libva-wayland2:amd64                          2.7.0-2                               amd64        Video Acceleration (VA) API for Linux -- Wayland runtime
ii  libva-x11-2:amd64                             2.7.0-2                               amd64        Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva2:amd64                                  2.7.0-2                               amd64        Video Acceleration (VA) API for Linux -- runtime
ii  libvdpau1:amd64                               1.3-1ubuntu2                          amd64        Video Decode and Presentation API for Unix (libraries)
ii  libvpx6:amd64                                 1.8.2-1build1                         amd64        VP8 and VP9 video codec (shared library)
ii  libx264-155:amd64                             2:0.155.2917+git0a84d98-2             amd64        x264 video coding library
ii  libx265-179:amd64                             3.2.1-1build1                         amd64        H.265/HEVC video stream encoder (shared library)
ii  libxv1:amd64                                  2:1.0.11-1                            amd64        X11 Video extension library
ii  libxvidcore4:amd64                            2:1.3.7-1                             amd64        Open source MPEG-4 video codec (library)
ii  libxvmc1:amd64                                2:1.0.12-2                            amd64        X11 Video extension library
ii  libxxf86vm1:amd64                             1:1.1.4-1build1                       amd64        X11 XFree86 video mode extension library
ii  mesa-va-drivers:amd64                         20.0.8-0ubuntu1~20.04.1               amd64        Mesa VA-API video acceleration drivers
ii  mesa-vdpau-drivers:amd64                      20.0.8-0ubuntu1~20.04.1               amd64        Mesa VDPAU video acceleration drivers
ii  va-driver-all:amd64                           2.7.0-2                               amd64        Video Acceleration (VA) API -- driver metapackage
ii  vdpau-driver-all:amd64                        1.3-1ubuntu2                          amd64        Video Decode and Presentation API for Unix (driver metapackage)
ii  vlc-plugin-video-output:amd64                 3.0.9.2-1                             amd64        multimedia player and streamer (video output plugins)
ii  vlc-plugin-video-splitter:amd64               3.0.9.2-1                             amd64        multimedia player and streamer (video splitter plugins)
ii  xserver-xorg-video-all                        1:7.7+19ubuntu14                      amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amdgpu                     19.1.0-1                              amd64        X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-ati                        1:19.1.0-1                            amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-fbdev                      1:0.5.0-1ubuntu1                      amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel                      2:2.99.917+git20200226-1              amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                    1:1.0.16-1                            amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-qxl                        0.1.5+git20200331-1                   amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-radeon                     1:19.1.0-1                            amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-vesa                       1:2.4.0-2                             amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                     1:13.3.0-3                            amd64        X.Org X server -- VMware display driver
```
```

amel@laptopasus:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 8a12 (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Iris Plus Graphics G7 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 8a03 (rev 03)
00:14.0 USB controller: Intel Corporation Ice Lake-LP USB 3.1 xHCI Host Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Device 34ef (rev 30)
00:14.3 Network controller: Intel Corporation Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW) (rev 30)
00:14.5 SD Host controller: Intel Corporation Ice Lake-LP SD Controller (rev 30)
00:15.0 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #0 (rev 30)
00:15.1 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #1 (rev 30)
00:16.0 Communication controller: Intel Corporation Management Engine Interface (rev 30)
00:17.0 SATA controller: Intel Corporation Ice Lake-LP SATA Controller [AHCI mode] (rev 30)
00:1d.0 PCI bridge: Intel Corporation Device 34b4 (rev 30)
00:1e.0 Communication controller: Intel Corporation Ice Lake-LP Serial IO UART Controller #0 (rev 30)
00:1e.2 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO SPI Controller #0 (rev 30)
00:1f.0 ISA bridge: Intel Corporation Ice Lake-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Smart Sound Technology Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Ice Lake-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP SPI Controller (rev 30)
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a809
```

---

### Post by deadflowr on 2020-10-27
The driver package is
```
ii  xserver-xorg-video-intel                      2:2.99.917+git20200226-1              amd64        X.Org X server -- Intel i8xx, i9xx display driver
```
Look at
```
inxi -Gxz
```
for some more basic info about the graphics drivers in use.

---

### Post by Yellow Pasque on 2020-10-28
The "driver" is broken into several pieces, which have seemingly conflicting and confusing names. Luckily, intel users shouldn't need to worry about that.

Kernel module: i915
2D/Xserver driver: modesetting/glamor
3D driver: "Iris" Mesa/Gallium3D
Video decode/encode accelerator: i965-va-driver

> **deadflowr said:**
> The driver package is xserver-xorg-video-intel
Probably not. Nowadays, Xserver uses built-in modesetting driver (aka glamor) for modern Intel GPU's.

---

