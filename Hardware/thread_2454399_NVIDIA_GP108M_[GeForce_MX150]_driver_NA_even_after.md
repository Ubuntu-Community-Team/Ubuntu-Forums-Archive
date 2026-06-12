---
title: "NVIDIA GP108M [GeForce MX150] driver: N/A even after installation and reboot (multipl"
date: 2020-11-28
forum: Hardware
---

### Post by leo56 on 2020-11-28
hello

I'm a noob (got this out of the way)
recently installed ubuntu 20.04
cant get nvidia driver to work (activate)

current status:
```

leo@Leo:~$ inxi -G
Graphics:  Device-1: Intel UHD Graphics 620 driver: i915 v: kernel 
           Device-2: NVIDIA GP108M [GeForce MX150] driver: N/A 
           Device-3: Chicony HD WebCam type: USB driver: uvcvideo 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 3072x1728~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) 
           v: 4.6 Mesa 21.0.0-devel (git-4cce4d2 2020-11-27 focal-oibaf-ppa) 
```


tried these:
```

sudo apt-get purge nvidia*
sudo apt-get install nvidia-prime
ubuntu-drivers install nvidia-driver-455
prime-select nvidia
reboot

```


some info:

```

 leo@Leo:~$ lspci -nnk | egrep -A3 -i "3D|VGA"
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 620 [8086:5917] (rev 07)
    Subsystem: Acer Incorporated [ALI] UHD Graphics 620 [1025:1193]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 3D controller [0302]: NVIDIA Corporation GP108M [GeForce MX150] [10de:1d10] (rev a1)
    Subsystem: Acer Incorporated [ALI] GP108M [GeForce MX150] [1025:119a]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)

```


```

leo@Leo:~$ ls /lib/modprobe.d/
aliases.conf  blacklist_linux_5.4.0-54-generic.conf  blacklist_linux_5.4.0-56-generic.conf  fbdev-blacklist.conf  nvidia-graphics-drivers.conf    nvidia-kms.conf  systemd.conf

```


```

leo@Leo:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                 0.8-8ubuntu0.20.04.1                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                     3.2.1-22                              amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                              3.2.1-22                              amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libnvidia-cfg1-455:amd64                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-455                          455.45.01-0ubuntu0.20.04.1            all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-450-server:amd64            450.80.02-0ubuntu0.20.04.3            amd64        NVIDIA libcompute package
ii  libnvidia-compute-455:amd64                   455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-compute-455:i386                    455.45.01-0ubuntu0.20.04.1            i386         NVIDIA libcompute package
ii  libnvidia-decode-455:amd64                    455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-455:i386                     455.45.01-0ubuntu0.20.04.1            i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-455:amd64                    455.45.01-0ubuntu0.20.04.1            amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-455:i386                     455.45.01-0ubuntu0.20.04.1            i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-455:amd64                     455.45.01-0ubuntu0.20.04.1            amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-455:amd64                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-455:i386                       455.45.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-455:amd64                        455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-455:i386                         455.45.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-455:amd64                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-455:i386                       455.45.01-0ubuntu0.20.04.1            i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-455                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA compute utilities
ii  nvidia-dkms-455                               455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA DKMS package
ii  nvidia-driver-455                             455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-455                      455.45.01-0ubuntu0.20.04.1            amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-455                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.14                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               440.82-0ubuntu0.20.04.1               amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-455                              455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18build1                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-455                 455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA binary Xorg driver


```


```

leo@Leo:~$ mokutil --sb-state
SecureBoot enabled

```


what can be done here?
thank you

---

### Post by Bashing-om on 2020-11-28
leo56; Hello

As the Nvidia driver is considered 3rd party - the firmware is doing its job to block it.
as we have:
> 
leo@Leo:~$ mokutil --sb-state
SecureBoot enabled

 Try again and see what results with secure boot disabled in the firmware:
```

sudo apt autoremove --purge nvidia-*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot = all good now ?

If all good then one may re-enable secure boot.

[INDENT]maybe Yes
[/INDENT]

---

### Post by leo56 on 2020-11-28
i see

well since the main purpose isn't to install this driver but to solve this problem of this GPU not being used 
what is the safest solution here ? 
is disabling the secure boot going to be a problem later in any way ?
if yes , how do I switch to external GPU ?

since while in nvidiaXserver the external GPU (performance mode) is selected,  I  know this GPU is not being used is not websites that have a little  rendering are real slow while just scrolling , or all the windows are  jittery when I move them

my main question is how do I solve this jittery windows and slow GPU renderings?

---

### Post by leo56 on 2020-11-29
well I tried disabling secure boot , and purged nvidia* and all , and this is now:

```

leo@Leo:~$ mokutil --sb-state
SecureBoot enabled
SecureBoot validation is disabled in shim

```

and this is what i get:

```

leo@Leo:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-modules-nvidia-455-generic-hwe-20.04 : Depends: nvidia-kernel-common-455 (<= 455.38-1) but 455.45.01-0ubuntu0.20.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```


tried the manual way:
```

leo@Leo:~$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001D10sv00001025sd0000119Abc03sc02i00
vendor   : NVIDIA Corporation
model    : GP108M [GeForce MX150]
driver   : nvidia-driver-450 - distro non-free
driver   : nvidia-driver-440-server - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-455 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin


leo@Leo:~$ sudo ubuntu-drivers install nvidia-driver-455
No drivers found for installation.

```


why? :D

---

### Post by Bashing-om on 2020-11-29
leo56; Hummmm ...

We have:
> 
sysop@2004x-c:~$ apt list nvidia-kernel-common-455
Listing... Done
nvidia-kernel-common-455/focal-updates [color=green]455.38-0ubuntu0.20.04.1 [/color]amd64


BUT:
> 
sysop@2004x-c:~$ apt list linux-generic-hwe-20.04
Listing... Done
linux-generic-hwe-20.04/focal-updates 5.4.0.54.57 amd64
//
sysop@2004x-c:~$ apt depends linux-modules-nvidia-455-generic-hwe-20.04
linux-modules-nvidia-455-generic-hwe-20.04
  Depends: linux-modules-nvidia-455-5.4.0-54-generic (= 5.4.0-54.60)
  Depends: nvidia-kernel-common-455 ([color=red]<= 455.38-1[/color])
  Depends: nvidia-kernel-common-455 (>= 455.38)
sysop@2004x-c:~$ apt list nvidia-driver-455
Listing... Done
nvidia-driver-455/focal-updates [color=green]455.38-0ubuntu0.20.04.1 [/color]amd64


So that begs the question of what you have installed.

What shows:
```

lsb_release -a
uname -r
dpkg -l | grep -i nvidia
dpkg -l | grep linux-
apt policy nvidia-kernel-common-455

```

[INDENT][INDENT]we are all only too human, however there are answers
[/INDENT][/INDENT]

---

### Post by leo56 on 2020-11-30
idrk honestly :D

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal


$ uname -r
5.4.0-56-generic

$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                 0.8-8ubuntu0.20.04.1                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                     3.2.1-22                              amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                              3.2.1-22                              amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libnvidia-cfg1-455:amd64                      455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA binary OpenGL/GLX configuration library
rc  libnvidia-compute-450-server:amd64            450.80.02-0ubuntu0.20.04.3            amd64        NVIDIA libcompute package
ii  libnvidia-compute-455:amd64                   455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  nvidia-prime                                  0.8.14                                all          Tools to enable NVIDIA's Prime
ii  xserver-xorg-video-nvidia-455                 455.45.01-0ubuntu0.20.04.1            amd64        NVIDIA binary Xorg driver

$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu                     2.34-6ubuntu1                         amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu3.1                          all          Linux image base package
ii  linux-firmware                                1.187.6                               all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                       5.4.0.56.59                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.4.0-54                        5.4.0-54.60                           all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-54-generic                5.4.0-54.60                           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-56                        5.4.0-56.62                           all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-56-generic                5.4.0-56.62                           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04               5.4.0.56.59                           amd64        Generic Linux kernel headers
rc  linux-image-5.4.0-42-generic                  5.4.0-42.46                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-54-generic                  5.4.0-54.60                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-56-generic                  5.4.0-56.62                           amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.4.0.56.59                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-56.62                           amd64        Linux Kernel Headers for development
rc  linux-modules-5.4.0-42-generic                5.4.0-42.46                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-54-generic                5.4.0-54.60                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-56-generic                5.4.0-56.62                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-54-generic          5.4.0-54.60                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-56-generic          5.4.0-56.62                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                  all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.04~git20190206.bf6db5b4+dfsg1-2   all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                  amd64        Bootloader for Linux/i386 using MS-DOS floppies




$ apt policy nvidia-kernel-common-455
nvidia-kernel-common-455:
  Installed: (none)
  Candidate: 455.45.01-0ubuntu0.20.04.1
  Version table:
     455.45.01-0ubuntu0.20.04.1 500
        500 http://archive.ubuntu.com/ubuntu focal-proposed/multiverse amd64 Packages
     455.45.01-0ubuntu0~0.20.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal/main amd64 Packages
     455.38-0ubuntu0.20.04.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages

```

---

### Post by Bashing-om on 2020-11-30
leo56; Oh !

How about that BumbleBee and nvidia-prime are in conflict.
BumbleBee is depreciated in favor of -prime.

I do suggest we try purging BumbleBee - see what happens with installing -prime:
```

sudo apt purge bumble*
sudo apt install --reinstall nvidia-prime

```

[INDENT]gots to be a reason
[/INDENT]

---

### Post by leo56 on 2020-11-30
thank you for the quick responses &#10084;&#65039;

don't really have much to say :D
here's the result :

```
$ sudo apt-get purge bumble*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'bumblebee-nvidia' for glob 'bumble*'
Note, selecting 'bumblebee' for glob 'bumble*'
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms primus-libs
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  bumblebee* bumblebee-nvidia*
0 upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
After this operation, 239 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 246761 files and directories currently installed.)
Removing bumblebee-nvidia (3.2.1-22) ...
Removing bumblebee (3.2.1-22) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.3) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-56-generic
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=879d7e0f-6176-4ecd-9f23-52638cb9860f)
I: Set the RESUME variable to override this.
(Reading database ... 246728 files and directories currently installed.)
Purging configuration files for bumblebee (3.2.1-22) ...
Purging configuration files for bumblebee-nvidia (3.2.1-22) ...
Processing triggers for systemd (245.4-4ubuntu3.3) ...



$ sudo apt-get install --reinstall nvidia-prime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms primus-libs
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 8 not upgraded.
Need to get 0 B/9,164 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 246721 files and directories currently installed.)
Preparing to unpack .../nvidia-prime_0.8.14_all.deb ...
Unpacking nvidia-prime (0.8.14) over (0.8.14) ...
Setting up nvidia-prime (0.8.14) ...



$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-modules-nvidia-455-generic-hwe-20.04 : Depends: nvidia-kernel-common-455 (<= 455.38-1) but 455.45.01-0ubuntu0.20.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Bashing-om on 2020-11-30
leo56; Humm ..

Not real sure what to make of this. 
See:
> 

sysop@2004x-c:~$ apt list xserver-xorg-hwe-18.04
Listing... Done
xserver-xorg-hwe-18.04/focal 3:14.5 amd64
//
sysop@2004x-c:~$ apt list xserver-xorg-hwe-20.04
Listing... Done


No Xstack for the HWE release ? What are they thinking here. Something changed - or just no longer needed as a separate package ?

Humm - something has changed as "xserver-xorg-hwe-16.04" is no longer in the repo.
> 
sysop@2004x-c:~$ apt list xserver-xorg-hwe-16.04
Listing... Done
sysop@2004x-c:~$

And the changelog does not provide what happened.
[http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg-hwe-16.04/xorg-hwe-16.04_7.7+16ubuntu3~16.04.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg-hwe-16.04/xorg-hwe-16.04_7.7+16ubuntu3~16.04.1/changelog)

In any event; can not install one graphic's driver without removing the prior driver first. Might give it a whirl
secure boot off
purge nvidia-*
autoinstall a driver once more.

All of our ducks in a row - see if we continue to define insanity - ( same thing, expecting a different result).

Depending on what happens with the re-install - what the package manager relates to us

[INDENT]dictates what we do next
[/INDENT]

---

### Post by leo56 on 2020-12-01
is this considered secure boot off?:

```

$ mokutil --sb-state
SecureBoot enabled
SecureBoot validation is disabled in shim

```

secure boot is greyed out in the BIOS, if this state is not what we want then I'll try to find how to disable it from BIOS
what do you suggest?

---

### Post by leo56 on 2020-12-01
well that was the problem
idk why secure boot being greyed out was a barrier in my mind like I can't do anything about thaaat &#128529;

followed this tutorial: [https://itsfoss.com/disable-secure-boot-in-acer/](https://itsfoss.com/disable-secure-boot-in-acer/)
disabled secure boot

and now:

```

$ mokutil --sb-state
SecureBoot disabled

```

then these worked perfectly:
```

$ sudo ubuntu-drivers autoinstall
$ sudo apt update
$ sudo apt upgrade
$ sudo prime-select nvidia
$ reboot

```

and now:
```

$ inxi -G
Graphics:  Device-1: Intel UHD Graphics 620 driver: i915 v: kernel 
           Device-2: NVIDIA GP108M [GeForce MX150] driver: nvidia v: 455.45.01 
           Device-3: Chicony HD WebCam type: USB driver: uvcvideo 
           Display: x11 server: X.Org 1.20.8 driver: modesetting,nvidia resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce MX150/PCIe/SSE2 v: 4.6.0 NVIDIA 455.45.01

```


awesome


thank you&#10084;&#65039;

---

### Post by leo56 on 2020-12-01
now the real problem I had which I tought was because of no GPU driver is still there
windows are flickering when I move them or scrolling through pages (firefox browesr with hardware acc. off and on tested).

did some research but there isn't a solution that worked for me

tried loging in on wayland (it wasn't named wayland though , the new option that was added for me was Xorge sth)
and xsrever settings are incomplete in nvidia-settings : [I]image attached
[/I]


what do you suggest ? i'm confused now
thank you

---

### Post by Bashing-om on 2020-12-01
leo56; Progress :) never-the-less

OK - is X happy ?
show:
```

sudo lshw -C display

```

And is the kernel also in a happy state with the Nvidia/Intel drivers ?
show
```

cat /var/log/gpu-manager.log

```

Before we go to push
[INDENT]make sure we have a foundation to push from
[/INDENT]

---

### Post by leo56 on 2020-12-02
:D YES

X says:
```

$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: UHD Graphics 620
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:131 memory:b2000000-b2ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GP108M [GeForce MX150]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:134 memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128)

```



and :

```

$ cat /var/log/gpu-manager.log
Disabled by kernel parameter "nogpumanager"

```

---

### Post by Yellow Pasque on 2020-12-02
I would suggest trying to use ondemand mode. This will run everything on the Intel GPU except for the programs you specify to run on the Nvidia GPU with prime-run. You will get better power consumption and battery life this way. And if you're trying to use Wayland, it should run better on the Intel GPU anyway.

Use the following commands to save typing in the future:
```
echo "alias prime-run=__NV_PRIME_RENDER_OFFLOAD=1 __VK_LAYER_NV_optimus=NVIDIA_only __GLX_VENDOR_LIBRARY_NAME=nvidia" >> ~/.bashrc
source ~/.bashrc
```

and try changing to "on-demand" mode:
```
sudo prime-select on-demand
```

Reboot to make sure it takes effect.

Verification (first command should show Intel or AMD and second command Nvidia):
```
glxinfo -B
prime-run glxinfo -B
```

If all goes well, you can run programs on the Nvidia GPU by prefixing the command with "prime-run" as in the glxinfo example above.

---

### Post by leo56 on 2020-12-06
I tried this but doesn't seem to solve the issue

take a look at the attached image

firefox and gnome and all the programs run automatically on nvidia when I'm in performance mode
but still the tears happen , and it seems to only affect the moving the windows and scrolls and not the pre-programmed animations like maximizing a window , minimizing ...

any suggestions? 

thank you

---

### Post by Yellow Pasque on 2020-12-07
> **leo56 said:**
> I tried this but doesn't seem to solve the issue

Just to verify it worked, can you run 'prime-select ondemand' and log out/in, and then look at the output from the commands.

```
glxinfo -B
prime-run glxinfo -B
```

---

### Post by leo56 on 2020-12-08
```
**$ glxinfo -B**
name of display: :1
display: :1  screen: 0
direct rendering: Yes
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 2048 MB
    Total available memory: 2048 MB
    Currently available dedicated video memory: 1810 MB
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce MX150/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 455.45.01
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6.0 NVIDIA 455.45.01
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)

OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 455.45.01
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20





**leo@Leo:~$ prime-run glxinfo -B**
name of display: :1
display: :1  screen: 0
direct rendering: Yes
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 2048 MB
    Total available memory: 2048 MB
    Currently available dedicated video memory: 1811 MB
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce MX150/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 455.45.01
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6.0 NVIDIA 455.45.01
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)

OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 455.45.01
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
```

both are nvidia it seems

---

### Post by Yellow Pasque on 2020-12-08
Then ondemand mode is not working, or you did not enter it correctly. You are still stuck in nvidia/"performance" mode. Unfortunately, I don't have an Nvidia/Optimus laptop and haven't gotten too in-depth with it. Maybe you will have more luck here: [https://forums.developer.nvidia.com/c/gpu-unix-graphics/linux/148](https://forums.developer.nvidia.com/c/gpu-unix-graphics/linux/148)

---

