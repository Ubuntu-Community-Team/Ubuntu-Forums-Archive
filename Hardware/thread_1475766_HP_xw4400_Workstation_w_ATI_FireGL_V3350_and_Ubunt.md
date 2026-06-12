---
title: "HP xw4400 Workstation w/ ATI FireGL V3350 and Ubuntu 10.04 amd64"
date: 2010-05-07
forum: Hardware
---

### Post by marxlv on 2010-05-07
Hi!

I have a question about hardware support for ATI FireGL V3350 video card in Ubuntu 10.04 amd64.
lspci:
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV515GL [FireGL V3350]
01:00.1 Display controller: ATI Technologies Inc RV515GL [FireGL V3350] (Secondary)

```lsmod | grep radeon:
```

radeon                739595  2 
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
drm                   198770  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon

```glxgears:
```

4309 frames in 5.0 seconds
4508 frames in 5.0 seconds
4508 frames in 5.0 seconds
4504 frames in 5.0 seconds
4508 frames in 5.0 seconds
4508 frames in 5.0 seconds
4508 frames in 5.0 seconds
4508 frames in 5.0 seconds
4505 frames in 5.0 seconds

```aptitude search fglrx:
```

p   fglrx                                                                             - Video driver for the ATI graphics accelerators                                              
p   fglrx-amdcccle                                                                    - Catalyst Control Center for the ATI graphics accelerators                                   
p   fglrx-dev                                                                         - Video driver for the ATI graphics accelerators (devel files)                                
p   fglrx-kernel-source                                                               - Transitional package for fglrx-kernel-source                                                
p   fglrx-modaliases                                                                  - Identifiers supported by the ATI graphics driver                                            
p   xorg-driver-fglrx                                                                 - Transitional package for xorg-driver-fglrx  

```The question is: what is the best driver option for my current setup? I am not worried about gaming 3D performance, but more about Google Earth, media player (mplayer, vlc ...) performance.
I have tried installing ATI drivers from homepage fglrx-8.583, but as I understand they do not work with Ubuntu 10.04 and the support for V3350 is dropped in newer versions. Am I right on this one?
Installing fglrx via aptitude results in black screen with some random pink pixels on top of the screen and no keyboard/mouse.

--
Marx.

---

### Post by dino99 on 2010-05-07
xserver-xorg-video-radeonhd

---

### Post by marxlv on 2010-05-07
> **dino99 said:**
> xserver-xorg-video-radeonhd

Thnaks! Installed that, but not sure if it got picked up. After several reboots, lsmod ouput stays the same:
```

radeon                739595  2 
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
drm                   198770  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon

```Any additional tips to get xserver-xorg-video-radeonhd running? Is there a way to verify that I use the correct driver? I tried purging xserver-xorg-video-radeon but that only broke dual monitor capability and removed xserver-xrog-video-ati package.

--
Marx.

P.S. I read Community Ubuntu RadeonHD Documentation [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) It tells to use xorg.conf which I think is deprecated. Or can I still use it in Ubuntu 10.04?

---

