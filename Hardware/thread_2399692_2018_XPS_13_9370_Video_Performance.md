---
title: "2018 XPS 13 9370 Video Performance"
date: 2018-08-28
forum: Hardware
---

### Post by blackfire on 2018-08-28
Hello,
 I'm struggling to diagnose a rather annoying issue with video playback on my Dell XPS 13 Developer Edition (9370).
Video playback is jittery - I can notice it skipping frames. It happens every few seconds both in fullscreen and in window mode.
I'm at loss so suggestions warmly welcome.

I'm running Ubuntu 18.04.1.
uname -r is 4.15.0-33-generic
Kernel module seems loaded OK (see below for lspci) as i915 shows up in lsmod.
I'm running with 200% scaling in gnome and 3840x2160, but I have not seen any difference scaling down resolution and removing the Scale factor (i.e. setting to 100%). I did not restart X between these tests though.
glxgears reports ~60 FPS

```

sudo lspci -nnk | grep -i vga -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 620 [8086:5917] (rev 07)
	Subsystem: Dell UHD Graphics 620 [1028:07e6]
	Kernel driver in use: i915
	Kernel modules: i915

```

```
env | grep LIB shows up empty
glxinfo shows direct rendering enabled and     Device: Mesa DRI Intel(R) UHD Graphics 620 (Kabylake GT2)  (0x5917)

```

glmark2, for the curious
```
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) UHD Graphics 620 (Kabylake GT2) 
    GL_VERSION:    3.0 Mesa 18.0.5
=======================================================
[build] use-vbo=false: FPS: 3779 FrameTime: 0.265 ms
[build] use-vbo=true: FPS: 4195 FrameTime: 0.238 ms
[texture] texture-filter=nearest: FPS: 2673 FrameTime: 0.374 ms
[texture] texture-filter=linear: FPS: 3029 FrameTime: 0.330 ms
[texture] texture-filter=mipmap: FPS: 3446 FrameTime: 0.290 ms
[shading] shading=gouraud: FPS: 2976 FrameTime: 0.336 ms
[shading] shading=blinn-phong-inf: FPS: 2984 FrameTime: 0.335 ms
[shading] shading=phong: FPS: 2153 FrameTime: 0.464 ms
[shading] shading=cel: FPS: 1654 FrameTime: 0.605 ms
[bump] bump-render=high-poly: FPS: 1735 FrameTime: 0.576 ms
[bump] bump-render=normals: FPS: 3623 FrameTime: 0.276 ms
[bump] bump-render=height: FPS: 3422 FrameTime: 0.292 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1854 FrameTime: 0.539 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1068 FrameTime: 0.936 ms
[pulsar] light=false:quads=5:texture=false: FPS: 3015 FrameTime: 0.332 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 796 FrameTime: 1.256 ms
[desktop] effect=shadow:windows=4: FPS: 1155 FrameTime: 0.866 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 711 FrameTime: 1.406 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 707 FrameTime: 1.414 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 943 FrameTime: 1.060 ms
[ideas] speed=duration: FPS: 1707 FrameTime: 0.586 ms
[jellyfish] <default>: FPS: 1901 FrameTime: 0.526 ms
[terrain] <default>: FPS: 232 FrameTime: 4.310 ms
[shadow] <default>: FPS: 1753 FrameTime: 0.570 ms
[refract] <default>: FPS: 580 FrameTime: 1.724 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2773 FrameTime: 0.361 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 2422 FrameTime: 0.413 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 2515 FrameTime: 0.398 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 2129 FrameTime: 0.470 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 2413 FrameTime: 0.414 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 2628 FrameTime: 0.381 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 2372 FrameTime: 0.422 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 2592 FrameTime: 0.386 ms
=======================================================
                                  glmark2 Score: 2179 
=======================================================
```

---

### Post by Yellow Pasque on 2018-08-29
What program are you trying to use for playback?
Also, check vainfo:
```
sudo apt-get install vainfo
vainfo
```

^Note: please use code tags like that when pasting output from commands/terminal.

---

### Post by blackfire on 2018-08-29
Hey Temujin,
 oh sorry, poor practice on my side to not use the code tags.
Thanks for taking the time to reply.
Didn't know about vainfo but can't see anything wrong with it either - I'm not sure how to read the VA-API version but the driver seems to be the right one.

I can see this issue while using Netflix on the latest Chrome stable, but the issue is also noticeable when I use glmark2 and (somewhat less) on glxgears. I have to admit sometimes I have the impression there is that "skip second" even when I just scroll a complex web page, but that might just be me being primed now.

```

libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Kaby Lake - 2.1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSliceLP
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointEncSliceLP
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointEncSliceLP
      VAProfileH264MultiviewHigh      :	VAEntrypointVLD
      VAProfileH264MultiviewHigh      :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileH264StereoHigh         :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD
      VAProfileJPEGBaseline           :	VAEntrypointEncPicture
      VAProfileVP8Version0_3          :	VAEntrypointVLD
      VAProfileVP8Version0_3          :	VAEntrypointEncSlice
      VAProfileHEVCMain               :	VAEntrypointVLD
      VAProfileHEVCMain               :	VAEntrypointEncSlice
      VAProfileHEVCMain10             :	VAEntrypointVLD
      VAProfileHEVCMain10             :	VAEntrypointEncSlice
      VAProfileVP9Profile0            :	VAEntrypointVLD
      VAProfileVP9Profile0            :	VAEntrypointEncSlice
      VAProfileVP9Profile2            :	VAEntrypointVLD

```

---

### Post by Yellow Pasque on 2018-08-29
^vainfo looks good.

I don't know about Chrome. You may need to jump through hoops to get video decode accel:
[https://phoronix.com/scan.php?page=news_item&px=Chrome-VA-API-Nears](https://phoronix.com/scan.php?page=news_item&px=Chrome-VA-API-Nears)
[https://chromium-review.googlesource.com/c/chromium/src/+/532294](https://chromium-review.googlesource.com/c/chromium/src/+/532294)

---

### Post by blackfire on 2018-08-29
So you pointed me in the right direction - thank you!. I've checked with chrome media internals and indeed I was using the Ffmpeg decoding. 
For future readers: I used a chromium version from PPA which has the  VA-API support built in [as suggested by: [https://www.pcsuggest.com/chromium-hardware-accelerated-video-decoding-linux/]](https://www.pcsuggest.com/chromium-hardware-accelerated-video-decoding-linux/])
Sadly though it did nothing for netflix as it's using the encrypted playback renderer which does not seem to be smart enough, via widevine, to go through hw acceleration.
So no real solution here.

I think this explains at least why I have crappy netflix performance (and generally delivers a lesson on the importance on not using Intel GPUs on high end laptops running Ubuntu)

However, I'm still not clear on why I'm observing the same behavior outside of Chrome - that seems bizarre.

---

