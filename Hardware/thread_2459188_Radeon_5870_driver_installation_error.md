---
title: "Radeon 5870 driver installation error"
date: 2021-03-12
forum: Hardware
---

### Post by derek28 on 2021-03-12
20.04 Focal Fossa
Long time but low level Linux user and enthusiast.
Thanks in advance for advice/assistance. 

I've used Ubuntu and this graphics card with success before but reinstalled ubuntu yesterday on this setup. I have no onboard graphic output ports. Currently I have an old dell monitor and a Sony Trinitron CRT TV connected, both via DVI. During installation the display was mirrored on both devices but now there is no output from the tv and it's not detected by the display settings at all. Here's the output for sudo lshw -c video

  ```
*-display UNCLAIMED       
       description: VGA compatible controller
       product: Cypress XT [Radeon HD 5870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fbbc0000-fbbdffff ioport:b000(size=256) memory:c0000-dffff
```

I downloaded tar file amdgpu-pro-20.20-1098277-ubuntu-20.04 from AMD's website. First I tried ./amdgpu-install which returned similar error messages to the output below. After running amdgpu-uninstall I tried amdgpu-pro-install. Here's the errors in the output:

```
Setting up amdgpu-dkms (1:5.6.0.15-1098277) ...
Loading new amdgpu-5.6.0.15-1098277 DKMS files...
Building for 5.8.0-44-generic
Building for architecture x86_64
Building initial module for 5.8.0-44-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms.0.c
rash'
Error! Bad return status for module build on kernel: 5.8.0-44-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.6.0.15-1098277/build/make.log for more informatio
n.
dpkg: error processing package amdgpu-dkms (--configure):
 installed amdgpu-dkms package post-installation script subprocess returned erro
r exit status 10
dpkg: dependency problems prevent configuration of amdgpu:
 amdgpu depends on amdgpu-dkms (= 1:5.6.0.15-1098277); however:
  Package amdgpu-dkms is not configured yet.

dpkg: error processing package amdgpu (--configure):
 dependency problems - leaving unconfigured
Setting up xserver-xorg-amdgpu-video-amdgpu (1:19.1.0-1098277) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          Setting up mesa-amdgpu-omx-drivers:amd64 (1:20.0.5-109
8277) ...
Setting up libegl1-amdgpu-mesa:amd64 (1:20.0.5-1098277) ...
Setting up libegl1-amdgpu-mesa:i386 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-glx:amd64 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-glx:i386 (1:20.0.5-1098277) ...
Setting up amdgpu-pro-core (20.20-1098277) ...
Setting up libgles2-amdgpu-mesa:amd64 (1:20.0.5-1098277) ...
Setting up libgles2-amdgpu-mesa:i386 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-dri:amd64 (1:20.0.5-1098277) ...
Setting up libgl1-amdgpu-mesa-dri:i386 (1:20.0.5-1098277) ...
Setting up vulkan-amdgpu-pro:amd64 (20.20-1098277) ...
update-alternatives: using /opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd64.json to pr
ovide /etc/vulkan/icd.d/amd_icd64.json (amd_icd64.json) in auto mode
Setting up vulkan-amdgpu-pro:i386 (20.20-1098277) ...
update-alternatives: using /opt/amdgpu-pro/etc/vulkan/icd.d/amd_icd32.json to pr
ovide /etc/vulkan/icd.d/amd_icd32.json (amd_icd32.json) in auto mode
Setting up libosmesa6-amdgpu:amd64 (1:20.0.5-1098277) ...
Setting up libosmesa6-amdgpu:i386 (1:20.0.5-1098277) ...
dpkg: dependency problems prevent configuration of amdgpu-pro:
 amdgpu-pro depends on amdgpu (= 20.20-1098277); however:
  Package amdgpu is not configured yet.

dpkg: error processing package amdgpu-pro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amdgpu-pro-lib32:
 amdgpu-pro-lib32 depends on amdgpu (= 20.20-1098277) | amdgpu-hwe (= 20.20-1098
277); however:
  Package amdgpu is not configured yet.
  Package amdgpu-hwe is not installed.
 amdgpu-pro-lib32 depends on amdgpu-pro (= 20.20-1098277) | amdgpu-pro-hwe (= 20
.20-1098277); however:
  Package amdgpu-pro is not configured yet.
  Package amdgpu-pro-hwe is not installed.

dpkg: error processing package amdgpu-pro-lib32 (--configure):
 dependency problems - leaving unconfigured
Setting up libglapi1-amdgpu-pro:amd64 (20.20-1098277) ...
No apport report written because the error message indicates its a followup erro
r from a previous failure.
                          No apport report written because MaxReports is reached
 already
        Setting up libglapi1-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-dri:amd64 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-dri:i386 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-appprofiles (20.20-1098277) ...
Setting up libegl1-amdgpu-pro:amd64 (20.20-1098277) ...
Setting up libegl1-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libegl1-amdgpu-mesa-drivers:amd64 (1:20.0.5-1098277) ...
Setting up libegl1-amdgpu-mesa-drivers:i386 (1:20.0.5-1098277) ...
Setting up libgles2-amdgpu-pro:amd64 (20.20-1098277) ...
Setting up libgles2-amdgpu-pro:i386 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-glx:amd64 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-glx:i386 (20.20-1098277) ...
Setting up libgl1-amdgpu-pro-ext:amd64 (20.20-1098277) ...
Setting up amdgpu-lib (20.20-1098277) ...
Setting up amdgpu-lib32 (20.20-1098277) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Errors were encountered while processing:
 amdgpu-dkms
 amdgpu
 amdgpu-pro
 amdgpu-pro-lib32
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QIII on 2021-03-12
amdgpu and AMDGPU-PRO will not work with that card.  There was no reason to install it and it might be best to remove it.

Your 5870 is supported by the open source Radeon driver, which is included in the kernel as a module.  There is no reason to install anything.  In fact, at install time, the Ubuntu installer detects whether the radeon or amdgpu module supports your GPU and loads the appropriate kernel module without having to do anything.

So, the first -- pardon the simplicity -- thing to do is check all the cables and be sure they are connected well.  Try re-seating the card.

---

### Post by deadflowr on 2021-03-12
Look like you made a mess of the package management system.
What does
```
dpkg -l | grep amdgpu
```
show?

Edit:
You might luck out and be able to just run an apt or dpkg command to remove the four listed packages,
amdgpu-pro
amdgpu-dkms
amdgpu
amdgpu-pro-lib32

---

### Post by derek28 on 2021-03-12
Okay thank you for clearing that bit up for me. Uninstalling right now. I've just checked the cables and they're plenty secure, just as they were during install. The main issue I'm trying to resolve is getting no output on the TV, even though it gave an output during installation. After the first post-installation boot the TV seems to have become invisible. I assumed this was some kind of driver issue.

---

### Post by derek28 on 2021-03-12
```
ii  libdrm-amdgpu1:amd64                       2.4.102-1ubuntu1~20.04.1            amd64        Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-amdgpu1:i386                        2.4.102-1ubuntu1~20.04.1            i386         Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  xserver-xorg-video-amdgpu                  19.1.0-1                            amd64        X.Org X server -- AMDGPU display driver
```

---

### Post by deadflowr on 2021-03-12
> **derek28 said:**
> ```
ii  libdrm-amdgpu1:amd64                       2.4.102-1ubuntu1~20.04.1            amd64        Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-amdgpu1:i386                        2.4.102-1ubuntu1~20.04.1            i386         Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  xserver-xorg-video-amdgpu                  19.1.0-1                            amd64        X.Org X server -- AMDGPU display driver
```

Looks like the problem packages aren't listed, so that should be good.

I'd run an apt update and apt full-upgrade to check nothing's broke.
```
sudo apt update
sudo apt full-upgrade
```

---

### Post by derek28 on 2021-03-12
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra dctrl-tools dkms gstreamer1.0-vaapi
  libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386
  libffi7:i386 libgstreamer-plugins-bad1.0-0 libllvm11:i386
  libomxil-bellagio-bin libomxil-bellagio0 libstdc++6:i386 libva-wayland2
  libva2:i386 libvdpau1:i386 libwayland-client0:i386 libwayland-egl1:i386
  libwayland-server0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386
  libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386
  libxxf86vm1:i386 mesa-vdpau-drivers:i386 vdpau-driver-all:i386
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```

---

### Post by deadflowr on 2021-03-12
Everything looks good.
autoremove is completely optional.
You don't have to remove them if you don't want to.

---

### Post by derek28 on 2021-03-12
Any idea what I should do to try and get output on the CRT display?

---

### Post by mastablasta on 2021-03-15
try to select xorg at login.

another option is to add display manually. this should not be needed as Radeon should recognise the monitor. i mean you say it worked during install (using same radeon drivers) and now it doesn't recognise the monitor at all or it sees the TV and just the picture is not displaying? 

modern cards otherwise use EDID from the monitor to setup their display and refresh rates. older monitors (let alone TV) sometimes didn't send EDID or they are not recognised. in this case you say you had mirrored image, but i wonder if refresh rate and all that was the same or different and if that could be causing just the picture not to appear.

display manager (at the start) can also be a factor here.

---

