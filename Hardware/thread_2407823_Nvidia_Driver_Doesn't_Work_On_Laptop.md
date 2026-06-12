---
title: "Nvidia Driver Doesn't Work On Laptop"
date: 2018-12-10
forum: Hardware
---

### Post by RedChili on 2018-12-10
All right, so here's my problem:

I have a brand new HP Pavilion Power 15-CB084NO laptop with a Nvidia  Geforce GTX 1050 graphics card, and I&#8217;m trying to use an external  monitor connected via HDMI. When I'm in &#8220;Software & Updates /  Additional Drivers,&#8221; it says that I nvidia-driver-390, -396, -410 and -415 installed. I've chosen to use nvidia-driver-415.

But no matter what I do, the computer is still using the Intel driver, meaning that I cannot get the external monitor to work, which is a major hassle for me.

I first tried running Ubuntu Mate 18.04, but when I couldn't fix the problem there, I was recommended to switch to the regular Ubuntu 18.04. But unfortunately, that hasn't helped at all.

The result of "cat /var/log/gpu-manager.log" is:

```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-42-generic/updates/dkms
Found nvidia module: nvidia-modeset.ko
Looking for amdgpu modules in /lib/modules/4.15.0-42-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "on" in /sys/bus/pci/devices/0000:01:00.0/power/control
Loading nvidia with "no" parameters
```

The result of "dpkg -l | grep -i nvidia" is:

```
ii  libnvidia-cfg1-415:amd64                      415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-415                          415.18-0ubuntu0~gpu18.04.2                  all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-396:amd64                   396.54-0ubuntu0~gpu18.04.1                  amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                    396.54-0ubuntu0~gpu18.04.1                  i386         NVIDIA libcompute package
ii  libnvidia-compute-415:amd64                   415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-415:i386                    415.18-0ubuntu0~gpu18.04.2                  i386         NVIDIA libcompute package
ii  libnvidia-decode-415:amd64                    415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-415:i386                     415.18-0ubuntu0~gpu18.04.2                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-415:amd64                    415.18-0ubuntu0~gpu18.04.2                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-415:i386                     415.18-0ubuntu0~gpu18.04.2                  i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-415:amd64                      415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-415:i386                       415.18-0ubuntu0~gpu18.04.2                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-415:amd64                        415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-415:i386                         415.18-0ubuntu0~gpu18.04.2                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-415:amd64                      415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-415:i386                       415.18-0ubuntu0~gpu18.04.2                  i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  mate-optimus                                  18.04.0-1                                   all          MATE Desktop applet for controlling NVIDIA Optimus graphics cards
rc  nvidia-compute-utils-396                      396.54-0ubuntu0~gpu18.04.1                  amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-415                      415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA compute utilities
rc  nvidia-dkms-396                               396.54-0ubuntu0~gpu18.04.1                  amd64        NVIDIA DKMS package
ii  nvidia-dkms-415                               415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA DKMS package
ii  nvidia-driver-415                             415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-396                      396.54-0ubuntu0~gpu18.04.1                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-415                      415.18-0ubuntu0~gpu18.04.2                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-415                      415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.8.2                                     all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               415.18-0ubuntu0~gpu18.04.1                  amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-415                              415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-415                 415.18-0ubuntu0~gpu18.04.2                  amd64        NVIDIA binary Xorg driver


```

The result of "sudo lshw -C display" is:

```
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107M [GeForce GTX 1050 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107M [GeForce GTX 1050 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:131 memory:b2000000-b2ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff

       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:131 memory:b2000000-b2ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff

```

When I try to run nvidia-settings, I get the error message:

```
ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system

```

So, is there a way of fixing this problem? Or is there a way for me to use the external monitor even if I'm on the Intel driver?

Thanks in advance for all help!

---

### Post by Yellow Pasque on 2018-12-10
nvidia kernel module won't load. The first thing I would try is loading it manually and see what happens:
```
sudo modprobe -v nvidia
```

---

### Post by RedChili on 2018-12-11
Thanks for the suggestion, Temujin. The result is:

> insmod /lib/modules/4.15.0-42-generic/updates/dkms/nvidia.ko 
modprobe: ERROR: could not insert 'nvidia': Required key not available



---

### Post by RedChili on 2018-12-16
Is there anybody that can help me out with this problem?

---

### Post by ubname on 2018-12-16
Have you disabled secure boot in UEFI?
otherwise it wont work.

---

### Post by RedChili on 2018-12-17
Wow! That di the trick! I've been struggling with this problem for a long time, and I cannot believe that the solution was that simple. Thank you, Ubname!

---

