---
title: "radeon hd 2400 mobile gpu"
date: 2019-02-07
forum: Hardware
---

### Post by ikonomn on 2019-02-07
21:17:57 kernel: [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (65536, 2, 4096, -22)
21:17:57 kernel: [drm:radeon_ttm_backend_bind [radeon]] *ERROR* failed to bind 16 pages at 0x00000000
21:17:57 kernel: [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (65536, 2, 4096, -22)
21:17:57 kernel: [drm:radeon_ttm_backend_bind [radeon]] *ERROR* failed to bind 16 pages at 0x00000000
21:17:57 lightdm: PAM adding faulty module: pam_kwallet5.so
21:17:55 kernel: radeon 0000:01:00.0: disabling GPU acceleration
21:17:55 kernel: [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x8504)=0xCAFEDEAD)

I had all these errors and my laptop stopped boot, I had to boot using recovery mode. After some search on the web,   I found the following solution.

I download the xorg-xf86-video-ati from [URL="https://github.com/freedesktop/xorg-xf86-video-ati"]https://github.com/freedesktop/xorg-xf86-video-ati
[/URL]
I extracted the source to a **folder** and the I issued the following commands as root.

I hope I helped others with the same problem.

```
sudo apt-get install libtool
sudo apt-get install xorg-dev
sudo apt-get install libgbm-dev
./autogen.sh
./configure
make
sudo apt-get install texlive
make dist
sudo apt install checkinstall
sudo checkinstall
```

---

### Post by kle2 on 2020-01-06
Here follows a little addition about a similar "GEM object" problem at an **Radeon HD 3650** GPU. Tested in Kubuntu 18.04 LTS with latest official and unofficial MESA drivers.

It seems that several Radeon R600 GPU based graphics cards are affected by that issue. I noticed that error in conjunction with DVB TV watching. The H264 acceleration (through the UVD unit) is according to my results broken. I can confirm this behavior also for an Radeon 2400 XT and Radeon 2600 Pro, both at an iMac Aluminum. Whatever, I hope that this will be fixed in future Mesa versions.

Will try the "xorg-xf86-video-ati tweak" if I find the time... ;)

```

[ 3920.320825] [TTM] Illegal buffer object size
[ 3920.320834] [TTM] Illegal buffer object size
[ 3920.320910] [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (0, 6, 4096, -22)
[ 3920.321193] [TTM] Illegal buffer object size
[ 3920.321195] [TTM] Illegal buffer object size
[ 3920.321223] [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (0, 6, 4096, -22)

[ 4344.178317] [TTM] Illegal buffer object size
[ 4344.178327] [TTM] Illegal buffer object size
[ 4344.178406] [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (0, 6, 4096, -22)
[ 4344.178509] [TTM] Illegal buffer object size
[ 4344.178511] [TTM] Illegal buffer object size
[ 4344.178538] [drm:radeon_gem_object_create [radeon]] *ERROR* Failed to allocate GEM object (0, 6, 4096, -22)

```

---

