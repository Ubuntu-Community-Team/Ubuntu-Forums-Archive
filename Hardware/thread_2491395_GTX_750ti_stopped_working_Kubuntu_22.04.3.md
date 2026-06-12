---
title: "GTX 750ti stopped working Kubuntu 22.04.3"
date: 2023-10-06
forum: Hardware
---

### Post by chtorogu on 2023-10-06
Hello,

I put together a system with an i5 4460 and a GTX 750ti for my nephews to use. Everything worked just fine when I put it together and tested it. However, once I took it to them and got it up and running I started having graphical issues immediately. As I started it up I noticed that the graphics and text on the login screen was enormous and it remained like that after login. I checked the resolution and it was correct. The GUI sizing issue them solved itself somehow (but not in the login screen) and I figured all was well. I fired up Steam and tried several games with no problems. Then, suddenly, the signal to the screen died and I had to do a hard reboot (hadn't set up the keyboard shortcut for video reset.) After this nothing with 3d graphics work at all. Most games fail to launch and those that do run at like 1 fps.

I have tried several driver versions and I have tried reverting to older kernels but still the same. I then did a clean reinstall and was greeted with the giant GUI once more. Didn't have time to test games but something is clearly very wrong.

So I'm wondering if there's some issue with the GTX 750ti and (K)ubuntu 22.04(.3) or with the Nvidia drivers?

I'm thinking perhaps if I were to install the original Kubuntu 22.04 with the older and more tried and true kernel 5.15, I'd have better luck. However, I cannot find it anywhere. The links for the older 22.04 versions at kubuntu.org all lead to 22.04.3. Is it available anywhere?

Otherwise, does anyone recognize this issue and perhaps know of a solution (staying at the current version)?

Thanks in advance.

---

### Post by Bashing-om on 2023-10-06
chtorogu - Hello

Yeah do seem to be graphic's driver/hardware related.

Let's poke at it a bit and see what we can learn.
Hardware seen ?
```

lspci -k | grep -iEA5 'vga|3d'

```

Driver loaded ?
```

sudo lshw -C display

```

driver conflict ?
```

dpkg -l | grep -i nvidia 

```

Display manager happy ?
```

less /var/log/gpu-manager.log

```

[INDENT]see here what tales get told
[/INDENT]

---

### Post by chtorogu on 2023-10-07
Thanks a lot for your helpful reply.

I will try those commands the next time I go there. I'll write here once I do, will be within a few days.

---

### Post by Autodave on 2023-10-08
Don't ignore the obvious place to start.....have you tried another video cable?  Another monitor?  Are sure that the video card is fully installed?

---

### Post by chtorogu on 2023-10-09
The HDMI cable is brand new and appears to be working fine as there's no problem with the video output. I guess I could try another but I don't know why a bad cable would cause 3d rendering to fail but not 2d. I tried both hdmi ports on the card.

I did insert both the card and the PCI-e power fully and it did work for a few days then the 3d rendering stopped working. I guess the card could have malfunctioned but the fact that it worked perfectly then just failed completely without any signs that anything was wrong leads me to believe it's software related. There does seems to be something wonky with the driver as the desktop GUI renders as if the resolution is like 1024*768 even though it's set to 1920*1080 (the TV's native resolution.)

There's no other panel here to try with, could bring one but the actual video output seems fine.

Thanks for your advice.

Here's the output for the commands "Bashing-om" suggested:

```
[FONT=monospace][COLOR=#000000]lspci -k | grep -iEA5 'vga|3d'       [/COLOR]
01:00.0 [COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)[/COLOR]
        Subsystem: Gigabyte Technology Co., Ltd GM107 [GeForce GTX 750 Ti]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GM107 High Definition Audio Controller [GeForce 940MX] (rev a1)
        Subsystem: Gigabyte Technology Co., Ltd GM107 High Definition Audio Controller [GeForce 940MX][/FONT]
```

```
[FONT=monospace][COLOR=#000000]sudo lshw -C display[/COLOR]
[/FONT][FONT=monospace]
  *-display                  
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:32 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=1024,768[/FONT]
```

[FONT=monospace][COLOR=#000000]```
dpkg -l | grep -i nvidia

```[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]ii  lib[/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-cfg1-535:amd64                      535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] binary OpenGL/GLX configuration library[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-common-535                          535.113.01-0ubuntu0.22.04.1                 all          Shared files used by the [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] libraries[/COLOR]
rc  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-compute-525:amd64                   525.125.06-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] libcompute package[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-compute-535:amd64                   535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] libcompute package[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-compute-535:i386                    535.113.01-0ubuntu0.22.04.1                 i386         [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] libcompute package[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-decode-535:amd64                    535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] Video Decoding runtime libraries[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-decode-535:i386                     535.113.01-0ubuntu0.22.04.1                 i386         [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] Video Decoding runtime libraries[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-encode-535:amd64                    535.113.01-0ubuntu0.22.04.1                 amd64        NVENC Video Encoding runtime library[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-encode-535:i386                     535.113.01-0ubuntu0.22.04.1                 i386         NVENC Video Encoding runtime library[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-extra-535:amd64                     535.113.01-0ubuntu0.22.04.1                 amd64        Extra libraries for the [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] driver[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-fbc1-535:amd64                      535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] OpenGL-based Framebuffer Capture runtime library[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-fbc1-535:i386                       535.113.01-0ubuntu0.22.04.1                 i386         [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] OpenGL-based Framebuffer Capture runtime library[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-gl-535:amd64                        535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD[/COLOR]
ii  lib[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-gl-535:i386                         535.113.01-0ubuntu0.22.04.1                 i386         [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD[/COLOR]
rc  linux-modules-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-525-6.2.0-26-generic     6.2.0-26.26~22.04.1+2                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-26[/COLOR]
rc  linux-modules-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-525-6.2.0-34-generic     6.2.0-34.34~22.04.1+1                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-34[/COLOR]
ii  linux-modules-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-535-6.2.0-34-generic     6.2.0-34.34~22.04.1+1                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-34[/COLOR]
ii  linux-modules-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-535-generic-hwe-22.04    6.2.0-34.34~22.04.1+1                       amd64        Extra drivers for [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-535 for the generic-hwe-22.04 flavour[/COLOR]
ii  linux-objects-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-525-6.2.0-26-generic     6.2.0-26.26~22.04.1+2                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-26 (objects)[/COLOR]
ii  linux-objects-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-525-6.2.0-34-generic     6.2.0-34.34~22.04.1+1                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-34 (objects)[/COLOR]
ii  linux-objects-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-535-6.2.0-34-generic     6.2.0-34.34~22.04.1+1                       amd64        Linux kernel [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-34 (objects)[/COLOR]
ii  linux-signatures-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-6.2.0-26-generic      6.2.0-26.26~22.04.1+2                       amd64        Linux kernel signatures for [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-26-generic[/COLOR]
ii  linux-signatures-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-6.2.0-34-generic      6.2.0-34.34~22.04.1+1                       amd64        Linux kernel signatures for [/COLOR][COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000] modules for version 6.2.0-34-generic[/COLOR]
rc  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-compute-utils-525                      525.125.06-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] compute utilities[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-compute-utils-535                      535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] compute utilities[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-driver-535                             535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] driver metapackage[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-firmware-535-535.113.01                535.113.01-0ubuntu0.22.04.1                 amd64        Firmware files used by the kernel module[/COLOR]
rc  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-kernel-common-525                      525.125.06-0ubuntu0.22.04.1                 amd64        Shared files used with the kernel module[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-kernel-common-535                      535.113.01-0ubuntu0.22.04.1                 amd64        Shared files used with the kernel module[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-kernel-source-535                      535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] kernel source package[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-prime                                  0.8.17.1                                    all          Tools to enable [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000]'s Prime[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-settings                               510.47.03-0ubuntu1                          amd64        Tool for configuring the [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] graphics driver[/COLOR]
ii  [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-utils-535                              535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] driver support binaries[/COLOR]
ii  screen-resolution-extra                       0.18.2                                      all          Extension for the [COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-settings control panel[/COLOR]
ii  xserver-xorg-video-[COLOR=#FF5454]**nvidia**[/COLOR][COLOR=#000000]-535                 535.113.01-0ubuntu0.22.04.1                 amd64        [/COLOR][COLOR=#FF5454]**NVIDIA**[/COLOR][COLOR=#000000] binary Xorg driver[/COLOR][/FONT]
```

```
[FONT=monospace][COLOR=#000000]log_file: /var/log/gpu-manager.log[/COLOR]
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/6.2.0-34-generic/kernel
Looking for nvidia modules in /lib/modules/6.2.0-34-generic/kernel/nvidia-535srv
Looking for nvidia modules in /lib/modules/6.2.0-34-generic/kernel/nvidia-535
Found nvidia.ko module in /lib/modules/6.2.0-34-generic/kernel/nvidia-535/nvidia.ko
Looking for amdgpu modules in /lib/modules/6.2.0-34-generic/kernel
Looking for amdgpu modules in /lib/modules/6.2.0-34-generic/updates/dkms
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
Vendor/Device Id: 10de:1380
BusID "PCI:1@0:0:0"
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
Takes 0ms to wait for nvidia udev rules completed.
Single card detected
Nothing to do[/FONT]
```

Do you see anything wrong? I think I see why it's rendering the GUI so large as the resolution under "lshw --C display" is set to 1024*768. The monitor is at 1920*1080 though so the driver seems conflicted about that. Apps that use their own custom user interface render at correct size so it seems to just be KDE Plasma that thinks the resolution is 1024*768. Games work once more now after reinstall. But they did before too and then suddenly stopped working so that doesn't necessarily mean the problem is solved.

I would like to try an older version of 22.04 and see if that's more reliable. I have 22.04.1 and 22.04.2 on my machines and never had GPU driver problems. Those have 5 series kernels. The latter has a similar GPU, a  GTX 1050. Anyone know where the older versions can be found?

On a related note, the 22.04.02 release I have on my HTPC seems less stable driver wise than the 22.04.1 on my main PC. One day I booted it up and practically all drivers were gone (the nvidia drivers were still there but they were disabled.) I had to manually download (on another PC, as there was no network drivers on the HTPC) and install the appropriate linux-modules-extra package to get them back. QA problems creeping up at Ubuntu perhaps, like in most of the tech world. Hopefully not but that's a huge issue to just happen on it's own. Hadn't modified the system at all and no programs installed from outside built-in repository and from flathub, except for Mullvad VPN. It just broke on it's own, like with the PC in question in this thread.

---

### Post by #&amp;thj^% on 2023-10-09
> **chtorogu said:**
> 
I will try those commands the next time I go there. I'll write here once I do, will be within a few days.

Are we still waiting to see those?
```
sudo lshw -C display  ###First One
[sudo] password for me: 
  *-display                 
       description: VGA compatible controller
       product: Renoir
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: /dev/fb0
       version: c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list fb
       configuration: depth=32 driver=amdgpu latency=0 mode=1920x1080 resolution=1920,1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:1fa0-1f9f iomemory:1fa0-1f9f irq:46 memory:1fa50000000-1fa5fffffff memory:1fa60000000-1fa601fffff ioport:1000(size=256) memory:d1500000-d157ffff
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> dpkg -l | grep -i nvidia  ### Second one
ii  libnvidia-cfg1-535:amd64                          535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-535                              535.113.01-0ubuntu0.23.04.3                all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-535:amd64                       535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA libcompute package
ii  libnvidia-compute-535:i386                        535.113.01-0ubuntu0.23.04.3                i386         NVIDIA libcompute package
ii  libnvidia-decode-535:amd64                        535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-535:i386                         535.113.01-0ubuntu0.23.04.3                i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-535:amd64                        535.113.01-0ubuntu0.23.04.3                amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-535:i386                         535.113.01-0ubuntu0.23.04.3                i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-535:amd64                         535.113.01-0ubuntu0.23.04.3                amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-535:amd64                          535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-535:i386                           535.113.01-0ubuntu0.23.04.3                i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-535:amd64                            535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-535:i386                             535.113.01-0ubuntu0.23.04.3                i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  nvidia-common                                     1:0.9.7.1.1                                amd64        transitional package for ubuntu-drivers-common
ii  nvidia-compute-utils-535                          535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA compute utilities
ii  nvidia-dkms-535                                   535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA DKMS package
ii  nvidia-driver-535                                 535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA driver metapackage
ii  nvidia-firmware-535-535.113.01                    535.113.01-0ubuntu0.23.04.3                amd64        Firmware files used by the kernel module
ii  nvidia-kernel-common-535                          535.113.01-0ubuntu0.23.04.3                amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-535                          535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA kernel source package
ii  nvidia-prime                                      0.8.17.1                                   all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                   510.47.03-0ubuntu1                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-535                                  535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                           0.18.3                                     all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-535                     535.113.01-0ubuntu0.23.04.3                amd64        NVIDIA binary Xorg driver

```

---

### Post by chtorogu on 2023-10-09
Just adding another post to make "last post by" show that I have replied.

See reply above.

Again, thanks for any help.

---

### Post by #&amp;thj^% on 2023-10-09
Well I never would have noticed an edited Post, but post #7 showed up now.
I see this missing:
```
nvidia-dkms-535 
```
Is it installed?
show this:
```
apt policy nvidia-dkms-535 
```

---

### Post by Bashing-om on 2023-10-09
chtorogu; Well well well ...
Humm... What display compositor is at play here , Wayland, Xorg ? As Nvidia and Wayland still has its issues.
show us:
```

echo $XDG_SESSION_TYPE $DESKTOP_SESSION $XDG_SESSION_DESKTOP $XDG_CURRENT_DESKTOP
ps -efly | grep Xorg
systemctl status display-manager
xrandr -q

```

See if we need to consider a work-a-round for the resolution.

Edit:
Good catch 1fallen ^^


[INDENT]Seek, and ye shall find
[/INDENT]

---

### Post by chtorogu on 2023-10-10
Thanks, fellas. Will check the dkms issue next time I'm there and get back to you again. I can answer about the compositor, it's xorg. At least it was before reinstall. I checked because I thought the problem might be wayland. Do you have any ideas about how to work around the resolution issue?

---

### Post by #&amp;thj^% on 2023-10-10
This time to insure the driver is installed proper.
```
sudo apt autoremve --purge nvidia*
```
Now we cleaned up this mess.
```
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
```
For a re-install use:
```
sudo apt install nvidia-driver-535
sudo apt install nvidia-dkms
```
Reboot to your new driver.
And consider Bashing-om's warning "Nvidia and Wayland still has its issues." For best nVidia results use X11

---

### Post by chtorogu on 2023-10-17
I tried your suggestions and could not get it working. I also got a hold of an older version of 22.04 but it had the same issues. I then gave up on Kubuntu for this machine and installed Linux Mint and so far it works perfectly with no scaling issues and no problems with 3D graphics. I would guess Kubuntu (and possibly Ubuntu) currently has some driver issues with my GPU. Thanks a lot for all the help you've provided.

---

### Post by #&amp;thj^% on 2023-10-17
Thanks for the update, and happy you found a solution.

---

