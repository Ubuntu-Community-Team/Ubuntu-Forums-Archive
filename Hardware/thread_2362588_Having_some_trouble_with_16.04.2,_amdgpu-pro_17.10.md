---
title: "Having some trouble with 16.04.2, amdgpu-pro 17.10, and XFX RX 580"
date: 2017-05-30
forum: Hardware
---

### Post by dannygale on 2017-05-30
Hi everybody -- I'm having some trouble with ubuntu 16.04 and a pair of XFX RX 580 video cards I picked up recently. I had been using them on an oldish system that had a lot of bloat, so I started fresh with a completely reinstalled OS (I reused my existing home directory). It's ubuntu server 16.04.2 with ubuntu-desktop installed on top of it. Here's the details of the setup:

```
root@newton:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
root@newton:~# uname -a
Linux newton 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
root@newton:~# dpkg -l *amdgpu*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                  Architecture             Description
+++-======================================-========================-========================-=================================================================================
ii  amdgpu-pro                             17.10-414273             amd64                    Meta package to install amdgpu Pro components.
ii  amdgpu-pro-dkms                        17.10-414273             all                      amdgpu-pro driver in DKMS format.
ii  amdgpu-pro-lib32                       17.10-414273             amd64                    Meta package to support i386 runtime on amd64 architecture
ii  clinfo-amdgpu-pro                      17.10-414273             amd64                    AMD OpenCL info utility
ii  libdrm-amdgpu-pro-amdgpu1:amd64        1:2.4.70-414273          amd64                    Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-amdgpu-pro-amdgpu1:i386         1:2.4.70-414273          i386                     Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-amdgpu1:amd64                   2.4.70-1~ubuntu16.04.1   amd64                    Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-amdgpu1:i386                    2.4.70-1~ubuntu16.04.1   i386                     Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm2-amdgpu-pro:amd64               1:2.4.70-414273          amd64                    Userspace interface to kernel DRM services -- runtime
ii  libdrm2-amdgpu-pro:i386                1:2.4.70-414273          i386                     Userspace interface to kernel DRM services -- runtime
ii  libegl1-amdgpu-pro:amd64               17.10-414273             amd64                    implementation of the EGL API -- runtime
ii  libegl1-amdgpu-pro:i386                17.10-414273             i386                     implementation of the EGL API -- runtime
ii  libgbm1-amdgpu-pro:amd64               17.10-414273             amd64                    Generic buffer management API -- runtime
ii  libgbm1-amdgpu-pro:i386                17.10-414273             i386                     Generic buffer management API -- runtime
ii  libgbm1-amdgpu-pro-base                17.10-414273             all                      Generic buffer management API -- configuration files
ii  libgl1-amdgpu-pro-appprofiles          17.10-414273             all                      AMD OpenGL profiles configuration
ii  libgl1-amdgpu-pro-dri:amd64            17.10-414273             amd64                    implementation of the OpenGL API -- DRI modules
ii  libgl1-amdgpu-pro-dri:i386             17.10-414273             i386                     implementation of the OpenGL API -- DRI modules
ii  libgl1-amdgpu-pro-ext:amd64            17.10-414273             amd64                    xorg GLX exetnsion
ii  libgl1-amdgpu-pro-glx:amd64            17.10-414273             amd64                    implementation of the OpenGL API -- GLX runtime
ii  libgl1-amdgpu-pro-glx:i386             17.10-414273             i386                     implementation of the OpenGL API -- GLX runtime
ii  libgles2-amdgpu-pro:amd64              17.10-414273             amd64                    implementation of the OpenGL|ES 2.x API -- runtime
ii  libgles2-amdgpu-pro:i386               17.10-414273             i386                     implementation of the OpenGL|ES 2.x API -- runtime
ii  libopencl1-amdgpu-pro:amd64            17.10-414273             amd64                    AMD OpenCL ICD Loader library
ii  libopencl1-amdgpu-pro:i386             17.10-414273             i386                     AMD OpenCL ICD Loader library
ii  libvdpau-amdgpu-pro:amd64              1:13.0.3-414273          amd64                    AMDGPU Pro VDPAU driver
ii  libvdpau-amdgpu-pro:i386               1:13.0.3-414273          i386                     AMDGPU Pro VDPAU driver
un  libvdpau1-amdgpu-pro                   <none>                   <none>                   (no description available)
ii  opencl-amdgpu-pro-icd:amd64            17.10-414273             amd64                    non-free AMD OpenCL ICD Loaders
ii  opencl-amdgpu-pro-icd:i386             17.10-414273             i386                     non-free AMD OpenCL ICD Loaders
ii  vulkan-amdgpu-pro:amd64                17.10-414273             amd64                    AMDGPU Pro Vulkan driver
ii  vulkan-amdgpu-pro:i386                 17.10-414273             i386                     AMDGPU Pro Vulkan driver
un  xserver-xorg-video-amdgpu              <none>                   <none>                   (no description available)
ii  xserver-xorg-video-amdgpu-hwe-16.04    1.1.2-1~16.04.1          amd64                    X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-amdgpu-pro          1:1.2.99-414273          amd64                    X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-glamoregl-amdgpu-pr 1.18.3-414273            amd64                    X.Org X server -- graphics acceleration module based on OpenGL

```

Everything here seems to be OK, I think. 

The trouble is in dmesg: 
```

root@newton:~# dmesg | grep amdgpu
[    5.448632] [drm] amdgpu kernel modesetting enabled.
[    5.776283] fb: switching to amdgpudrmfb from VESA VGA
[    5.819779] amdgpu 0000:03:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[    5.819849] amdgpu 0000:03:00.0: VRAM: 8192M 0x0000000000000000 - 0x00000001FFFFFFFF (8192M used)
[    5.819854] amdgpu 0000:03:00.0: GTT: 8192M 0x0000000200000000 - 0x00000003FFFFFFFF
[    5.819943] [drm] amdgpu: 8192M of VRAM memory ready
[    5.819946] [drm] amdgpu: 8192M of GTT memory ready.
[    5.821163] amdgpu 0000:03:00.0: amdgpu: using MSI.
[    5.821180] [drm] amdgpu: irq initialized.
[    5.821194] amdgpu: [powerplay] amdgpu: powerplay sw initialized
[    5.821359] amdgpu 0000:03:00.0: fence driver on ring 0 use gpu addr 0x0000000200000008, cpu addr 0xffff94b117e3c008
[    5.821435] amdgpu 0000:03:00.0: fence driver on ring 1 use gpu addr 0x0000000200000018, cpu addr 0xffff94b117e3c018
[    5.821487] amdgpu 0000:03:00.0: fence driver on ring 2 use gpu addr 0x0000000200000028, cpu addr 0xffff94b117e3c028
[    5.821525] amdgpu 0000:03:00.0: fence driver on ring 3 use gpu addr 0x0000000200000038, cpu addr 0xffff94b117e3c038
[    5.821572] amdgpu 0000:03:00.0: fence driver on ring 4 use gpu addr 0x0000000200000048, cpu addr 0xffff94b117e3c048
[    5.821596] amdgpu 0000:03:00.0: fence driver on ring 5 use gpu addr 0x0000000200000058, cpu addr 0xffff94b117e3c058
[    5.821619] amdgpu 0000:03:00.0: fence driver on ring 6 use gpu addr 0x0000000200000068, cpu addr 0xffff94b117e3c068
[    5.821643] amdgpu 0000:03:00.0: fence driver on ring 7 use gpu addr 0x0000000200000078, cpu addr 0xffff94b117e3c078
[    5.821666] amdgpu 0000:03:00.0: fence driver on ring 8 use gpu addr 0x0000000200000088, cpu addr 0xffff94b117e3c088
[    5.821699] amdgpu 0000:03:00.0: fence driver on ring 9 use gpu addr 0x0000000200000098, cpu addr 0xffff94b117e3c098
[    5.821759] amdgpu 0000:03:00.0: fence driver on ring 10 use gpu addr 0x00000002000000a8, cpu addr 0xffff94b117e3c0a8
[    5.821789] amdgpu 0000:03:00.0: fence driver on ring 11 use gpu addr 0x00000002000000b8, cpu addr 0xffff94b117e3c0b8
[    5.822083] amdgpu 0000:03:00.0: fence driver on ring 12 use gpu addr 0x0000000001165420, cpu addr 0xffffb34dc2c5a420
[    5.822190] amdgpu 0000:03:00.0: fence driver on ring 13 use gpu addr 0x00000002000000d8, cpu addr 0xffff94b117e3c0d8
[    5.822217] amdgpu 0000:03:00.0: fence driver on ring 14 use gpu addr 0x00000002000000e8, cpu addr 0xffff94b117e3c0e8
**[    5.861978] amdgpu: [powerplay] [AVFS] Something is broken. See log!**
**[    5.863876] amdgpu: [powerplay] Can't find requested voltage id in vdd_dep_on_sclk table!**
**[    5.864918] amdgpu: [powerplay] VDDCI is larger than max VDDCI in VDDCI Voltage Table!**
[    5.900126] [drm] amdgpu: freesync_module init done ffff94b118c1c3e0.
[    6.063641] fbcon: amdgpudrmfb (fb0) is primary device
[    6.098048] amdgpu 0000:03:00.0: fb0: amdgpudrmfb frame buffer device
[    6.119330] [drm] Initialized amdgpu 3.9.0 20150101 for 0000:03:00.0 on minor 0
[    6.119380] amdgpu 0000:04:00.0: enabling device (0000 -> 0003)
[    6.476015] amdgpu 0000:04:00.0: VRAM: 8192M 0x0000000000000000 - 0x00000001FFFFFFFF (8192M used)
[    6.476779] amdgpu 0000:04:00.0: GTT: 8192M 0x0000000200000000 - 0x00000003FFFFFFFF
[    6.479082] [drm] amdgpu: 8192M of VRAM memory ready
[    6.479880] [drm] amdgpu: 8192M of GTT memory ready.
[    6.483538] amdgpu 0000:04:00.0: amdgpu: using MSI.
[    6.484382] [drm] amdgpu: irq initialized.
[    6.485218] amdgpu: [powerplay] amdgpu: powerplay sw initialized
[    6.486084] amdgpu 0000:04:00.0: fence driver on ring 0 use gpu addr 0x0000000200000008, cpu addr 0xffff94b121186008
[    6.486977] amdgpu 0000:04:00.0: fence driver on ring 1 use gpu addr 0x0000000200000018, cpu addr 0xffff94b121186018
[    6.487878] amdgpu 0000:04:00.0: fence driver on ring 2 use gpu addr 0x0000000200000028, cpu addr 0xffff94b121186028
[    6.488753] amdgpu 0000:04:00.0: fence driver on ring 3 use gpu addr 0x0000000200000038, cpu addr 0xffff94b121186038
[    6.489623] amdgpu 0000:04:00.0: fence driver on ring 4 use gpu addr 0x0000000200000048, cpu addr 0xffff94b121186048
[    6.490490] amdgpu 0000:04:00.0: fence driver on ring 5 use gpu addr 0x0000000200000058, cpu addr 0xffff94b121186058
[    6.491358] amdgpu 0000:04:00.0: fence driver on ring 6 use gpu addr 0x0000000200000068, cpu addr 0xffff94b121186068
[    6.492238] amdgpu 0000:04:00.0: fence driver on ring 7 use gpu addr 0x0000000200000078, cpu addr 0xffff94b121186078
[    6.493089] amdgpu 0000:04:00.0: fence driver on ring 8 use gpu addr 0x0000000200000088, cpu addr 0xffff94b121186088
[    6.493938] amdgpu 0000:04:00.0: fence driver on ring 9 use gpu addr 0x0000000200000098, cpu addr 0xffff94b121186098
[    6.494783] amdgpu 0000:04:00.0: fence driver on ring 10 use gpu addr 0x00000002000000a8, cpu addr 0xffff94b1211860a8
[    6.495622] amdgpu 0000:04:00.0: fence driver on ring 11 use gpu addr 0x00000002000000b8, cpu addr 0xffff94b1211860b8
[    6.497513] amdgpu 0000:04:00.0: fence driver on ring 12 use gpu addr 0x0000000001165420, cpu addr 0xffffb34dc225a420
[    6.499203] amdgpu 0000:04:00.0: fence driver on ring 13 use gpu addr 0x00000002000000d8, cpu addr 0xffff94b1211860d8
[    6.500136] amdgpu 0000:04:00.0: fence driver on ring 14 use gpu addr 0x00000002000000e8, cpu addr 0xffff94b1211860e8
**[    6.540642] amdgpu: [powerplay] [AVFS] Something is broken. See log!**
**[    6.542539] amdgpu: [powerplay] Can't find requested voltage id in vdd_dep_on_sclk table!**
[    6.583711] [drm] amdgpu: freesync_module init done ffff94b118837760.
[    6.733614] amdgpu 0000:04:00.0: No connectors reported connected with modes
[    6.740840] amdgpu 0000:04:00.0: fb1: amdgpudrmfb frame buffer device
[    6.754864] [drm] Initialized amdgpu 3.9.0 20150101 for 0000:04:00.0 on minor 1

```

The driver thinks something is broken. Where is the log it mentions here?

I'm using these cards to mine cryptocurrency and the hashrates I'm getting are almost 40% below expected for the RX580's. 

What's wrong here?

---

### Post by QIII on 2017-05-30
Hello!

What release of Ubuntu were you using previously?  Which driver?

The RX 580s are pretty new hardware.  You may or may not know that AMD is going through a very big project getting AMDGPU and AMDGPU-PRO up and running.  fglrx is discontinued for any Ubuntu release beyond 14.04.1 (and any other distro that uses a recent graphics stack.)  You seem to have at least AMDGPU installed.

However, since your hardware is so new, it may be that AMD has not completely caught up to it with the AMDGPU driver and some things may  not work.

Give me a bit.  I'm looking through my configs for any powerplay settings.

Edit:  I can't find anything specific to powerplay.  However, could you run a quick test?  If AMDGPU-PRO is running you should be able to get load information.  This is not exposed in AMDGPU yet:

```
cat /sys/kernel/debug/dri/64/amdgpu_pm_info | grep GPU\ Load | cut -c11-17
```

You may need to cut in a different spot.

I also see several bugs reported, but it will take me some time to research.  I won't have time for that until tomorrow at best.

---

### Post by dannygale on 2017-05-31
Hi QIII! Thanks for your quick response!

I am able to get load information, and it seems to align with what's actually happening. While running a benchmark, it comes back at 100%. After I've stopped the benchmark, it reports 0%. 

I am aware that they're going through some serious driver development effort right now. According to the 17.10 release notes, the 580's are supposed to be supported. 

Also worth mentioning: lsmod doesn't show amdgpu-pro, only amdgpu:
```
root@newton:~# lsmod | grep amd
amdkfd                139264  2
amd_iommu_v2           20480  1 amdkfd
amdgpu               2150400  6
amdttm                102400  1 amdgpu
amdkcl                 32768  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm_kms_helper        167936  1 amdgpu
drm                   368640  10 amdttm,amdgpu,amdkcl,drm_kms_helper
```

---

### Post by QIII on 2017-06-01
AMDGPU is all that will show.  The "-PRO" part is the proprietary goodness.

I do see several bugs related to this, but haven't had time to research.  I haven't seen such a thing with my 380X. 

In the interest of seeing if you can get sorted out, you might want to create a launchpad.org account (might as well use the same user name as you have here) and look through bug reports.

---

### Post by dannygale on 2017-06-01
Do you happen to have those bug IDs handy? I'll take a look through them and report back with what I find... thanks!

edit: I assume you mean Launchpad.net?

edit2: I must be searching in the wrong place or with the wrong keywords. I don't see anything that really seems to apply.

---

### Post by mörgæs on 2017-06-01
Thanks for your interest in reporting bugs. 

The developers' main focus is 17.10 so if your report is based upon testing in 17.10 (installed without reusing /home) you will have a better chance of getting noticed.

---

### Post by dannygale on 2017-06-01
> **mörgæs said:**
> Thanks for your interest in reporting bugs. 

The developers' main focus is 17.10 so if your report is based upon testing in 17.10 (installed without reusing /home) you will have a better chance of getting noticed.
My report is indeed based on 17.10. I don't really understand how maintaining /home could affect this but I will try with a completely fresh installation, after backing up my data, of course.

---

### Post by icmine on 2017-06-27
Hi, 

   I have the exact same problem. Xunbuntu 16.04 AMDGPU-Pro 17.10. I've tried Claymore and Ehtminer. Both had the same openCL driver not in list, no GPU found..
It has to be gpu driver issue. I'll update once I find anything :)

---

