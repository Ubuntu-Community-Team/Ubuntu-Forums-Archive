---
title: "Ubuntu nvidia-driver-* conflicts with NVME SSD"
date: 2018-06-26
forum: Hardware
---

### Post by 1.grayson.1 on 2018-06-26
[Edit: solved. Appears to be a HW issue - bad video card]

I have installed Ubuntu 18.04 on a new computer that has both a 250GB NVME SSD and a Geforce GTX 1050 Ti video card. When I attempt to install the NVIDIA drivers and then reboot, the system hangs indefinitely with a non-error message: "/dev/nvme0n1p2 clean, <blah> / <blah> files ...". When I boot into recovery mode, remove the NVIDIA drivers (via 'apt remove --purge nvidia-*'), and reboot, the system boots again to the desktop. The only difference is use of the NVIDIA drivers.


I have attempted use of the nvidia-drivers-390 and nvidia-drivers-396 (beta) packages with the same results.


I have attempted to use multiple PCIE slots for the video card with the same results.


Here is HW information about the NVME SSD:
```
:~$ hwinfo --storage
39: PCI 500.0: 0108 Non-Volatile memory controller (NVM Express)
  [Created at pci.378]
  Unique ID: Ddhb.RVN8AkDkdAE
  Parent ID: 1GTX.yRXtLzEGt06
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/0000:05:00.0
  SysFS BusID: 0000:05:00.0
  Hardware Class: storage
  Model: "Sandisk Non-Volatile memory controller"
  Vendor: pci 0x15b7 "Sandisk Corp"
  Device: pci 0x5002 
  SubVendor: pci 0x15b7 "Sandisk Corp"
  SubDevice: pci 0x5002 
  Driver: "nvme"
  Driver Modules: "nvme"
  Memory Range: 0x92b00000-0x92b03fff (rw,non-prefetchable)
  Memory Range: 0x92b04000-0x92b040ff (rw,non-prefetchable)
  IRQ: 16 (no events)
  Module Alias: "pci:v000015B7d00005002sv000015B7sd00005002bc01sc08i02"
  Driver Info #0:
    Driver Status: nvme is active
    Driver Activation Cmd: "modprobe nvme"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #40 (PCI bridge)
```


Here is HW info about the GFX card in PCIEx16 slot 1:
```
:~$ hwinfo --gfxcard
46: PCI 6500.0: 0300 VGA compatible controller (VGA)            
  [Created at pci.378]
  Unique ID: ze67.YOyOHBXROU8
  Parent ID: Iovz.ktE97HFsmdF
  SysFS ID: /devices/pci0000:64/0000:64:00.0/0000:65:00.0
  SysFS BusID: 0000:65:00.0
  Hardware Class: graphics card
  Model: "nVidia GP107 [GeForce GTX 1050 Ti]"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x1c82 "GP107 [GeForce GTX 1050 Ti]"
  SubVendor: pci 0x1458 "Gigabyte Technology Co., Ltd"
  SubDevice: pci 0x3733 
  Revision: 0xa1
  Driver: "nouveau"
  Driver Modules: "nouveau"
  Memory Range: 0xd7000000-0xd7ffffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (ro,non-prefetchable)
  Memory Range: 0xd0000000-0xd1ffffff (ro,non-prefetchable)
  I/O Ports: 0xb000-0xb07f (rw)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 52 (93249 events)
  Module Alias: "pci:v000010DEd00001C82sv00001458sd00003733bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #68 (PCI bridge)


Primary display adapter: #46
```


Here is HW info about the GFX card in PCIEx16 slot 2:
```
:~$ hwinfo --gfxcard
45: PCI 1700.0: 0300 VGA compatible controller (VGA)            
  [Created at pci.378]
  Unique ID: Ig0m.YOyOHBXROU8
  Parent ID: m862.ktE97HFsmdF
  SysFS ID: /devices/pci0000:16/0000:16:00.0/0000:17:00.0
  SysFS BusID: 0000:17:00.0
  Hardware Class: graphics card
  Model: "nVidia GP107 [GeForce GTX 1050 Ti]"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x1c82 "GP107 [GeForce GTX 1050 Ti]"
  SubVendor: pci 0x1458 "Gigabyte Technology Co., Ltd"
  SubDevice: pci 0x3733 
  Revision: 0xa1
  Driver: "nouveau"
  Driver Modules: "nouveau"
  Memory Range: 0xb4000000-0xb4ffffff (rw,non-prefetchable)
  Memory Range: 0xa0000000-0xafffffff (ro,non-prefetchable)
  Memory Range: 0xb0000000-0xb1ffffff (ro,non-prefetchable)
  I/O Ports: 0x7000-0x707f (rw)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 52 (6166 events)
  Module Alias: "pci:v000010DEd00001C82sv00001458sd00003733bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #62 (PCI bridge)


Primary display adapter: #45
```


The system runs fine using the nouveau drivers. However, I'd like to use CUDA for some development items and thus need to get the NVIDIA drivers operational. Any thoughts/recommendations/input is appreciated.

---

### Post by Autodave on 2018-06-26
Where are you getting the Nvidia driver from?

---

### Post by 1.grayson.1 on 2018-06-26
> **Autodave said:**
> Where are you getting the Nvidia driver from?
390 straight from the default Ubuntu repos

```
:~$ apt show -a nvidia-driver-390Package: nvidia-driver-390
Version: 390.67-0ubuntu0~gpu18.04.1
Priority: optional
Section: libs
Source: nvidia-graphics-drivers-390
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
...
APT-Sources: http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
...
Package: nvidia-driver-390
Version: 390.48-0ubuntu3
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-390
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
...
APT-Sources: http://us.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages

```

396 from the graphics-drivers repo
```
:~$ apt show -a nvidia-driver-396
Package: nvidia-driver-396
Version: 396.24.02-0ubuntu0~gpu18.04.1
Priority: optional
Section: libs
Source: nvidia-graphics-drivers-396
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
...
APT-Sources: http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
```

Installed via Software & Updates -> Additional Drivers and via command line 'ubuntu-drivers autoinstall'. All produce the same result.

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; Hello -

Which desktop are you activating ? 
```

systemctl status gdm
echo $XDG_SESSION_TYPE

```

wayland ? Not a lot of support to this time with proprietarily nvidia. Try the X11 session ( gear at the password screen).

else post back:
```

cat /var/log/gpu-manager.log

```
here we see what the graphics manager has to relate.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by 1.grayson.1 on 2018-06-26
> [COLOR=#000000]Which desktop are you activating?[/COLOR]

```
**:~$ systemctl status gdm**&#9679; gdm.service - GNOME Display Manager
   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)
   Active: active (running) since Tue 2018-06-26 10:29:56 EDT; 2h 46min ago
 Main PID: 944 (gdm3)
    Tasks: 3 (limit: 4915)
   CGroup: /system.slice/gdm.service
           &#9492;&#9472;944 /usr/sbin/gdm3


Jun 26 10:29:56 blah systemd[1]: Starting GNOME Display Manager...
Jun 26 10:29:56 blah systemd[1]: Started GNOME Display Manager.
Jun 26 10:29:56 blah gdm-launch-environment][950]: pam_unix(gdm-launch-environment:session): session open
Jun 26 10:30:04 blah gdm-password][1293]: pam_unix(gdm-password:session): session opened for user blah
**:~$ echo $XDG_SESSION_TYPE**
x11

```

> [COLOR=#000000]else post back[/COLOR]
```
:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-23-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-23-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1c82
BusID "PCI:23@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-DVI-D-1
output 1:
    card0-HDMI-A-2
output 2:
    card0-HDMI-A-3
output 3:
    card0-HDMI-A-1
Number of connected outputs for /dev/dri/card0: 4
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

Note these are results with the nouveau driver in place as the system won't boot with the NVIDIA driver in place.

---

### Post by 1.grayson.1 on 2018-06-26
I was able to boot into a recovery shell with the NVIDIA drivers installed. Here is the log from that:
```
:~$ cat gpu-manager.nvidia.log log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-23-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/4.15.0-23-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
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
Vendor/Device Id: 10de:1c82
BusID "PCI:23@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; Well ..

X11 so the driver "should" load - as it does not we need to find the why.
The next obvious thing to check and get out of the way - as this is a new machine == EFI == secure Boot ..
Is secure boot disabled in the firmware (bios) ?

[INDENT][INDENT]the hunt is on
[/INDENT][/INDENT]

---

### Post by 1.grayson.1 on 2018-06-26
Yes, secure boot was enabled (and booting correctly using the nouveau driver). I disabled secure boot, reinstalled the nvidia driver, and got the same result. I removed the nvidia driver again and booted fine back to the desktop.

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; K -

Should workie :(

OK, so what is now installed for nvidia - if anything ?
```

dpkg -l | grep -i nvidia

```
next up make sure the slate is clean .. then we try the proprietary driver install again and then we read X's instructions .

[INDENT][INDENT]Gotta be a reason
[/INDENT][/INDENT]

---

### Post by 1.grayson.1 on 2018-06-26
```
:~$ dpkg -l | grep -i nvidiaii  libnvidia-common-396                       396.24.02-0ubuntu0~gpu18.04.1       all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.48-0ubuntu3                     amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.48-0ubuntu3                     i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                 396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA libcompute package
ii  libnvidia-gl-396:amd64                     396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD


:~# apt remove --purge libnvidia-*
:~# apt remove --purge libnvidia-compute-*:i386


:~$ dpkg -l | grep -i nvidia
:~$


:~# ubuntu-drivers autoinstall


:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-396:amd64                   396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                       396.24.02-0ubuntu0~gpu18.04.1       all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-396:amd64                396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                 396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64                 396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386                  396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64                 396.24.02-0ubuntu0~gpu18.04.1       amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386                  396.24.02-0ubuntu0~gpu18.04.1       i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64                   396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386                    396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                     396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                      396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64                   396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386                    396.24.02-0ubuntu0~gpu18.04.1       i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-396                   396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA compute utilities
ii  nvidia-dkms-396                            396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA DKMS package
ii  nvidia-driver-396                          396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-396                   396.24.02-0ubuntu0~gpu18.04.1       amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396                   396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8                               all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            396.24-0ubuntu0~gpu18.04.1          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                           396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396              396.24.02-0ubuntu0~gpu18.04.1       amd64        NVIDIA binary Xorg driver
```

Same result.

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; Humm ...

I fully expect 18.04 to fully support NVME however, will not hurt to explicitly declare it in a grub boot parameter to pass to the kernel.
```

nvme_load=YES

```

also .. make sure in the firmware that the SATA setting is AHCI.

the installed packages look to be the same as mine ( 18.10/nvidia390).

Getting closer to having to read the instructions. 

as still
[INDENT][INDENT]we just do not know enough
[/INDENT][/INDENT]

---

### Post by 1.grayson.1 on 2018-06-26
So, here's some fun info. Without making any changes other changes, I reinstalled the NVIDIA drivers and rebooted. This time, I unplugged all of my monitors except for 1. They system booted with the NVIDIA driver.

I then plugged in my other monitors 1 at a time (1st into DVI port of video card, 2nd into 1st HDMI port, 3rd into 2nd HDMI port, 4th into 3rd HDMI port). When I got to the 4th one (of 4), connecting it via HDMI did not work. The screen remained black. However, connecting via Display Port DID work. That got my 4 monitors functional.

Thinking the 3rd HDMI port was somehow causing the issue, and now with 4 monitors working (again DVI, HDMI#1, HDMI#2, DisplayPort), I rebooted. Same issue on boot - it hung. I again disconnected all but the first monitor and rebooted. This time it booted back to the desktop. Seems as though something related to the monitors being connected at boot is causing it to hang. Any ideas?

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; Ho boy ..

Nope .. multi-monitors are not in my range of experience .. though I am aware there are issues in such an arrangement.
Maybe submit a bug report - and see what the big boys have to say ?

[INDENT][INDENT]a know-it-all
[INDENT][INDENT]I am not
[/INDENT][/INDENT]l[/INDENT][/INDENT]

---

### Post by 1.grayson.1 on 2018-06-26
I'm investigating it more from a HW perspective. It may be a bad video card, as it appears the HDMI#3 port doesn't work regardless of the connection configuration - even with a single monitor.

I appreciate all the help! At this point I'd consider it closed as a SW issue. I'm going to see if I can RMA the video card.

---

### Post by Bashing-om on 2018-06-26
1.grayson.1; Ho kay ..

Is sure a possibility that the signal at the card is kaput  O'scope to the rescue :)

If this matter is now concluded to your satisfaction -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]come back and let us know
[/INDENT][/INDENT]

---

