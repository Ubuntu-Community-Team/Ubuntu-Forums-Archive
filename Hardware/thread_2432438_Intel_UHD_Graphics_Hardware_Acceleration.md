---
title: "Intel UHD Graphics Hardware Acceleration"
date: 2019-12-02
forum: Hardware
---

### Post by ozzzman on 2019-12-02
Hello  :D

Anyone have any luck getting Intel UHD hardware accelerated video decoding to work?

I'm currently running Ubuntu 19.10 (Eoan Ermine).
Machine is an HP Envy x360 with Core i5-10210U.

Here's some input/output info:

inxi -G
```
Graphics:
Device-1: Intel driver: i915 v: kernel
Display: x11 server: X.Org 1.20.5 driver: i915 resolution: 1920x1080~60Hz
OpenGL: renderer: Mesa DRI Intel UHD Graphics (Comet Lake 3x8 GT2)
v: 4.5 Mesa 19.2.1 
```

lspci
```
00:00.0 Host bridge: Intel Corporation Device 9b61 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Device 9b41 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Device 02f9
00:13.0 Serial controller: Intel Corporation Device 02fc
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:14.3 Network controller: Intel Corporation Device 02f0
00:15.0 Serial bus controller [0c80]: Intel Corporation Device 02e8
00:15.1 Serial bus controller [0c80]: Intel Corporation Device 02e9
00:16.0 Communication controller: Intel Corporation Device 02e0
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode]
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Device 02b6 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Multimedia audio controller: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 02a4
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
06:00.0 Non-Volatile memory controller: Intel Corporation Device 0975 (rev 03)
0b:00.0 Non-Volatile memory controller: Intel Corporation Device 0975
```

vainfo
```
libva info: VA-API version 1.5.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_4
libva error: /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so init failed
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit[/QUOTE]

vdpauinfo
[QUOTE]display: :0 screen: 0
libva info: VA-API version 1.5.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_4
libva error: /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so init failed
libva info: va_openDriver() returns -1
API version: 1
Information string: OpenGL/VAAPI backend for VDPAU

Video surface:

name width height types
-------------------------------------------
420 4096 4096 NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8
422 4096 4096 NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8
444 4096 4096 NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8

Decoder capabilities:

name level macbs width height
----------------------------------------------------
MPEG1 --- not supported ---
MPEG2_SIMPLE --- not supported ---
MPEG2_MAIN --- not supported ---
H264_BASELINE --- not supported ---
H264_MAIN --- not supported ---
H264_HIGH --- not supported ---
VC1_SIMPLE --- not supported ---
VC1_MAIN --- not supported ---
VC1_ADVANCED --- not supported ---
MPEG4_PART2_SP --- not supported ---
MPEG4_PART2_ASP --- not supported ---
DIVX4_QMOBILE --- not supported ---
DIVX4_MOBILE --- not supported ---
DIVX4_HOME_THEATER --- not supported ---
DIVX4_HD_1080P --- not supported ---
DIVX5_QMOBILE --- not supported ---
DIVX5_MOBILE --- not supported ---
DIVX5_HOME_THEATER --- not supported ---
DIVX5_HD_1080P --- not supported ---
H264_CONSTRAINED_BASELINE --- not supported ---
H264_EXTENDED --- not supported ---
H264_PROGRESSIVE_HIGH --- not supported ---
H264_CONSTRAINED_HIGH --- not supported ---
H264_HIGH_444_PREDICTIVE --- not supported ---
HEVC_MAIN --- not supported ---
HEVC_MAIN_10 --- not supported ---
HEVC_MAIN_STILL --- not supported ---
HEVC_MAIN_12 --- not supported ---
HEVC_MAIN_444 --- not supported ---

Output surface:

name width height nat types
----------------------------------------------------
B8G8R8A8 16384 16384 -
R8G8B8A8 16384 16384 -
R10G10B10A2 16384 16384 -
B10G10R10A2 16384 16384 -
A8 16384 16384 -

Bitmap surface:

name width height
------------------------------
B8G8R8A8 16384 16384
R8G8B8A8 16384 16384
R10G10B10A2 16384 16384
B10G10R10A2 16384 16384
A8 16384 16384

Video mixer:

feature name sup
------------------------------------
DEINTERLACE_TEMPORAL -
DEINTERLACE_TEMPORAL_SPATIAL -
INVERSE_TELECINE -
NOISE_REDUCTION -
SHARPNESS -
LUMA_KEY -
HIGH QUALITY SCALING - L1 -
HIGH QUALITY SCALING - L2 -
HIGH QUALITY SCALING - L3 -
HIGH QUALITY SCALING - L4 -
HIGH QUALITY SCALING - L5 -
HIGH QUALITY SCALING - L6 -
HIGH QUALITY SCALING - L7 -
HIGH QUALITY SCALING - L8 -
HIGH QUALITY SCALING - L9 -

parameter name sup min max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH -
VIDEO_SURFACE_HEIGHT -
CHROMA_TYPE -
LAYERS -

attribute name sup min max
-----------------------------------------------------
BACKGROUND_COLOR -
CSC_MATRIX -
NOISE_REDUCTION_LEVEL -
SHARPNESS_LEVEL -
LUMA_KEY_MIN_LUMA -
LUMA_KEY_MAX_LUMA - 
```


glxinfo | grep -i opengl
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) UHD Graphics (Comet Lake 3x8 GT2)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.2.1
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 19.2.1
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.2.1
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

```

dmesg | grep -i i915
```
[ 27.942734] i915 0000:00:02.0: vgaarb: deactivate vga console
[ 27.946682] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+memwns=io+mem
[ 27.947525] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[ 27.983277] [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[ 28.044423] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[ 28.057074] fbcon: i915drmfb (fb0) is primary device
[ 28.082619] i915 0000:00:02.0: fb0: i915drmfb frame buffer device
```

I have gstreamer1.0-vaapi and libvdpau-va-gl1 installed.

I've tried installing the proprietary i965-va-driver-shaders and intel-media-va-driver-non-free packages (over i965-va-driver and intel-media-va-driver) and switched back again.

I've tried installing the oibaf PPA found here:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
(even tried switching the repository to 20.04 (Focal Fossa) to no avail).

I've also tried installing the upstream 5.4.1 kernel following this as a guide:
[https://www.tecmint.com/upgrade-kernel-in-ubuntu/](https://www.tecmint.com/upgrade-kernel-in-ubuntu/)


Nothing seems to work.  :confused:

---

### Post by TheFu on 2019-12-02
Some web searching found this: [https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-media-stack-on-Ubuntu](https://github.com/Intel-Media-SDK/MediaSDK/wiki/Intel-media-stack-on-Ubuntu) which is for 19.04 and appears to be the repo for Intel.

[https://wiki.ubuntu.com/IntelQuickSyncVideo](https://wiki.ubuntu.com/IntelQuickSyncVideo) says:
> If your CPU is Broadwell (5th gen) or older then disable 4K/VP9 support (to stop it from reverting to software playback): Create a configuration file .config/mpv/mpv.conf in your home directory that explicitly tells mpv to use acceleration and to download only formats that most Intel CPUs can decode in hardware:
```

 hwdec=vaapi
 ytdl-format="bestvideo[ext=mp4]+bestaudio[ext=m4a]"
```

But if your CPU is 7th gen (Kaby Lake) or newer then you probably don't want to do that because it will disable 4K/VP9/HDR support. Skylake systems (6th gen) are somewhere in the middle where the answer is mostly the same as for 7th gen but Skylake does not support HDR (and so would need the above workaround).

---

### Post by ozzzman on 2019-12-02
Thanks for the help TheFu.  I've found another answer.

sudo nano /etc/environment

add syntax:
LIBVA_DRIVER_NAME=iHD
(save and exit)
reboot

vainfo
```
libva info: VA-API version 1.5.0
libva info: va_getDriverName() returns 0
libva info: User requested driver 'iHD'
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_5
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.5 (libva 2.5.0)
vainfo: Driver version: Intel iHD driver - 1.0.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile2            :    VAEntrypointVLD
```

:guitar:

---

### Post by TheFu on 2019-12-03
Glad you found an answer AND posted it here!  Thanks!
Better to use 
```
sudoedit  /etc/environment
```
add syntax:
```
LIBVA_DRIVER_NAME=iHD
```
or just edit your own ~/.bashrc file
```
nano ~/.bashrc
``` Use any editor you like.
add syntax:
```
export LIBVA_DRIVER_NAME=iHD
```
While you are in the .bashrc file, might as well add a few other custom lines to specify a better PAGER and EDITOR you prefer.```

export PAGER=less
export EDITOR=gedit

```
less will let us go forwards and backwards while looking at files.
The editor will be used by sudoedit and other tools that honor it as your preferred editor.  Beware, if you use ssh logins, then specifying a GUI editor is a bad idea. There are some other options to control the editor depending on the type of login.

I need to find a workable solution for video HW decoding on my 16.04 desktops still.  I don't really want anything that needs a PPA.  mpv is the main video player here, so don't really need all that much broad support across programs.

---

### Post by papadolinux on 2020-01-16
Hello all!

Could I ask a kinda stupid question as a newbie I am? I came to this thread since I was trying to find a reason why my model of the GPU is not presented in my system/hardware settings. I have an integrated Intel UHD 620 and wherever i look only the i915 name shows. Mind you that I don't face any flickering issues or anything that can let me think that I don't have hardware acceleration in my system, but behold! I've run the above commands and i was getting the same errors as ozzzman, did what you guys suggested and now i can see the outcome running vainfo. 
So my question is this...Should I revert back to the previous state, or just leave the export LIBVA_DRIVER_NAME=iHD as is? Had my system already hardware acceleration?

Much appreciate any reply :)

---

