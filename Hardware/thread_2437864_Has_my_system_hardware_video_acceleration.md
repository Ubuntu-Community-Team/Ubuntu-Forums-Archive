---
title: "Has my system hardware video acceleration?"
date: 2020-03-02
forum: Hardware
---

### Post by papadolinux on 2020-03-02
Hello all,

Forgive me if I might open a similar thread, but I didn't get any solid answer. Or maybe I did and I didn't understand it since I am new to Linux. So, I am trying to see whether my system has video hardware acceleration. Please see below details of my system:

Kernel Version: 5.3.0-40-generic OS Type: 64-bit
 Processors: 8 × Intel® Core™ i5-10210U CPU @ 1.60GHz
 Memory: 15,5 Gib of RAM


lspci
```

00:00.0 Host bridge: Intel Corporation Device 9b61 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Device 9b41 (rev 02)
00:12.0 Signal processing controller: Intel Corporation Device 02f9
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:15.0 Serial bus controller [0c80]: Intel Corporation Device 02e8
00:16.0 Communication controller: Intel Corporation Device 02e0
00:17.0 SATA controller: Intel Corporation Device 02d3
00:1c.0 PCI bridge: Intel Corporation Device 02bc (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Device 02b1 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Audio device: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 02a4
01:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
3b:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
40:00.0 Network controller: Intel Corporation Device 2723 (rev 1a)
45:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
```

inxi -G
```
Graphics:  Device-1: Intel driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: modesetting unloaded: fbdev,vesa tty: N/A 
           OpenGL: renderer: Mesa DRI Intel UHD Graphics (Comet Lake 3x8 GT2) v: 4.5 Mesa 19.2.8
```


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
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSliceLP
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileVP9Profile2            : VAEntrypointVLD
```

glxinfo | grep -i opengl
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) UHD Graphics (Comet Lake 3x8 GT2) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.2.8
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 19.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

dmesg | grep -i i915
```
[    1.862613] i915 0000:00:02.0: vgaarb: deactivate vga console
[    1.865239] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.865685] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    1.898794] [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[    1.939543] fbcon: i915drmfb (fb0) is primary device
[    1.939566] i915 0000:00:02.0: fb0: i915drmfb frame buffer device
[    4.766472] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
```

What do ya say, I'm OK or rendering - acceleration needs a push? :)

---

### Post by Yellow Pasque on 2020-03-02
**Yes**, the 3D accel and video decode accel output is correct.

---

### Post by papadolinux on 2020-03-02
> **Yellow Pasque said:**
> **Yes**, the 3D accel and video decode accel output is correct.

Many thanks for your reply!

---

