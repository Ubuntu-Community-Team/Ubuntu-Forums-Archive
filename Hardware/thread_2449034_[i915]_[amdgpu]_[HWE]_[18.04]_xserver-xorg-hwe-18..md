---
title: "[i915] [amdgpu] [HWE] [18.04] xserver-xorg-hwe-18.04 broke hardware acceleration"
date: 2020-08-18
forum: Hardware
---

### Post by parsonsandrew1 on 2020-08-18
I have been struggling to get my hybrid graphics (i915, amdgpu) to properly work in Ubuntu 18.04.

A few months ago, I installed the drivers from [ppa:oibaf/graphics-drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers"). While the Intel drivers seemed to work well, the ***DRI_PRIME=1*** (amdgpu) failed to function properly (***glxgears*** displayed a black screen, programs from Steam would not launch).

1. I decided to continue looking for graphics solutions
2. It came to my attention that Oibaf considers 18.04 obsolete and suggests using HWE.
3. An Ubuntu 20.04 live USB worked flawlessly with both cards.

Seeing that I am tied to 18.04 by our tech stack, I cannot move to 20.04. 

I ran the following, thinking that this would get me the "20.04 graphics experience" and everything would work thereafter.

```

$ sudo ppa-purge ppa:oibaf/graphics-drivers
$ sudo apt-get install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04
```

Both completed successfully.

After rebooting, I noticed that Chrome/Chromium and Electron applications (Slack, VS Code, Zoom even?) exhibit extreme flickering, ghosting, screen tearing, and general artifacting while hardware acceleration is enabled. This appears to be a significant regression from the Oibaf PPA drivers.[B]

Questions:[/B]

1. How can I remedy this?
2. Does it make sense to roll back to non-HWE packages? Like the standard kernel and the standard xserver-xorg drivers?
3. Should I go back to the [ppa:oibaf/graphics-drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers") package?
4. ***DRI_PRIME=1 glxgears*** still does not work, but at this point that is a secondary objective.

[HR][/HR]
```

linux-generic-hwe-18.04 (5.4.0.42.46~18.04.35)
xserver-xorg-hwe-18.04 (1:7.7+19ubuntu8~18.04.3)

&#10140;  ~ inxi -Gxxxz
Graphics:  Device-1: Intel vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:3ea0 
           Device-2: Advanced Micro Devices [AMD/ATI] Lexa XT [Radeon PRO WX 3100] vendor: Dell driver: amdgpu v: kernel 
           bus ID: 3b:00.0 chip ID: 1002:6985 
           Display: x11 server: X.Org 1.20.8 compositor: gnome-shell v: 3.28.4 driver: amdgpu,ati,intel 
           unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz s-dpi: 96 
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (WHL GT2) v: 4.6 Mesa 20.0.8 compat-v: 3.0 direct render: Yes 

&#10140;  ~ DRI_PRIME=1 inxi -Gxxxz
Graphics:  Device-1: Intel vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:3ea0 
           Device-2: Advanced Micro Devices [AMD/ATI] Lexa XT [Radeon PRO WX 3100] vendor: Dell driver: amdgpu v: kernel 
           bus ID: 3b:00.0 chip ID: 1002:6985 
           Display: x11 server: X.Org 1.20.8 compositor: gnome-shell v: 3.28.4 driver: amdgpu,ati,intel 
           unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz s-dpi: 96 
           OpenGL: renderer: AMD Radeon Pro WX3100 (POLARIS12 DRM 3.35.0 5.4.0-42-generic LLVM 9.0.1) v: 4.5 Mesa 19.2.2 
           direct render: Yes 

&#10140;  ~ lsb_release -rd                                           
Description:    Ubuntu 18.04.5 LTS
Release:    18.04

&#10140;  ~ uname -a       
Linux Precision-3540 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

&#10140;  ~ dpkg -l | grep xserver
ii  x11-xserver-utils                                     7.7+7build1                                      amd64        X server utilities
ii  xserver-common                                        2:1.19.6-1ubuntu4.4                              all          common files used by various X servers
ii  xserver-xephyr                                        2:1.19.6-1ubuntu4.4                              amd64        nested X server
rc  xserver-xorg                                          1:7.7+19ubuntu7.1                                amd64        X.Org X server
ii  xserver-xorg-amdgpu-video-amdgpu                      1:19.0.1-1011208                                 amd64        X.Org X server -- AMD/ATI Radeon display driver
rc  xserver-xorg-core                                     2:1.19.6-1ubuntu4.4                              amd64        Xorg X server - core server
ii  xserver-xorg-core-hwe-18.04                           2:1.20.8-2ubuntu2.2~18.04.1                      amd64        Xorg X server - core server
ii  xserver-xorg-hwe-18.04                                1:7.7+19ubuntu8~18.04.3                          amd64        X.Org X server
ii  xserver-xorg-input-all-hwe-18.04                      1:7.7+19ubuntu8~18.04.3                          amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-libinput-hwe-18.04                 0.28.1-1~18.04.1                                 amd64        X.Org X server -- libinput input driver
rc  xserver-xorg-legacy                                   2:1.19.6-1ubuntu4.4                              amd64        setuid root Xorg server wrapper
ii  xserver-xorg-legacy-hwe-18.04                         2:1.20.8-2ubuntu2.2~18.04.1                      amd64        setuid root Xorg server wrapper
ii  xserver-xorg-video-all-hwe-18.04                      1:7.7+19ubuntu8~18.04.3                          amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-amdgpu-hwe-18.04                   19.1.0-1~18.04.1                                 amd64        X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-ati-hwe-18.04                      1:19.1.0-1~18.04.1                               amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-fbdev-hwe-18.04                    1:0.5.0-1ubuntu1~18.04.1                         amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel-hwe-18.04                    2:2.99.917+git20171229-1ubuntu1~18.04.1          amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau-hwe-18.04                  1:1.0.16-1~18.04.1                               amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-qxl-hwe-18.04                      0.1.5-2build2~18.04.1                            amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-radeon-hwe-18.04                   1:19.1.0-1~18.04.1                               amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-vesa-hwe-18.04                     1:2.4.0-1~18.04.1                                amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware-hwe-18.04                   1:13.3.0-2build1~18.04.1                         amd64        X.Org X server -- VMware display driver

```

---

