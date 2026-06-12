---
title: "OpenCL not working with nvidia-331 and bumblebeed"
date: 2015-02-18
forum: Hardware
---

### Post by geenux2 on 2015-02-18
Hi,

I'm aware that there are load of threads about this, yet, after a full afternoon of trying I'm no closer to a solution.
I can't get nvidia-331, bumblebee and opencl to work together.

I'm using 
- Ubuntu Trusty: can't really use anything else due to some propietary libraries for work
- nvidia-331: can't use nvidia-current (nvidia-304) because I need Opengl 4.3 
- opencl
- Nvidia GTX 660M GPU

I have bumblenee fully working and setup as
```

# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d

## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-331
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-331:/usr/lib32/nvidia-331
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-331/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

```

With the above configuration, primusrun works perfectly:
```
 $ primusrun glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 4.3.0 NVIDIA 331.113
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL version string: 4.4.0 NVIDIA 331.113
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler

```


As far as nvidia is concerned, I have the following:
```
$ dpkg --get-selections | grep nvidia
bumblebee-nvidia                install
nvidia-304                    deinstall
nvidia-331                    install
nvidia-331-uvm                    install
nvidia-modprobe                    install
nvidia-opencl-icd-304                deinstall
nvidia-opencl-icd-331                install
nvidia-settings                    deinstall
nvidia-settings-331                install
 
```

The vendor file /etc/OpenCL/vendors/nvidia.icd contains
```
/usr/lib/x86_64-linux-gnu/libnvidia-opencl.so
```
Which is a symlink
```
$ ls -l /usr/lib/x86_64-linux-gnu/libnvidia-opencl.so
lrwxrwxrwx 1 root root 27 févr.  6 19:37 /usr/lib/x86_64-linux-gnu/libnvidia-opencl.so -> libnvidia-opencl.so.331.113

```
I tried with all variants of this that I could find, including libcuda.so.

And here is what libs I have for opencl
```
$ locate libnvidia-opencl
/usr/lib/i386-linux-gnu/libnvidia-opencl.so.1
/usr/lib/i386-linux-gnu/libnvidia-opencl.so.331.113
/usr/lib/x86_64-linux-gnu/libnvidia-opencl.so
/usr/lib/x86_64-linux-gnu/libnvidia-opencl.so.1
/usr/lib/x86_64-linux-gnu/libnvidia-opencl.so.331.113

$ locate libOpenCL.so
/usr/lib/x86_64-linux-gnu/libOpenCL.so
/usr/lib/x86_64-linux-gnu/libOpenCL.so.1
/usr/lib/x86_64-linux-gnu/libOpenCL.so.1.0.0
/usr/local/cuda-6.5/lib64/libOpenCL.so

```

Here is what happens when I try to lauch an opencl app (using darktable because it provides clear output on opencl initialisation).
```
$  primusrun darktable -d opencl
[opencl_init] opencl related configuration options:
[opencl_init] 
[opencl_init] opencl: 1
[opencl_init] opencl_library: ''
[opencl_init] opencl_memory_requirement: 768
[opencl_init] opencl_memory_headroom: 300
[opencl_init] opencl_device_priority: '*/!0,*/*/*'
[opencl_init] opencl_size_roundup: 16
[opencl_init] opencl_async_pixelpipe: 0
[opencl_init] opencl_synch_cache: 0
[opencl_init] opencl_number_event_handles: 25
[opencl_init] opencl_micro_nap: 1000
[opencl_init] opencl_use_pinned_memory: 0
[opencl_init] opencl_use_cpu_devices: 0
[opencl_init] opencl_avoid_atomics: 0
[opencl_init] opencl_omit_whitebalance: 0
[opencl_init] 
[opencl_init] trying to load opencl library: '<system default>'
[opencl_init] opencl library 'libOpenCL' found on your system and loaded
modprobe: FATAL: Module nvidia not found.
[opencl_init] could not get platforms: -1001
[opencl_init] FINALLY: opencl is NOT AVAILABLE on this system.
[opencl_init] initial status of opencl enabled flag is OFF.
 
```
The module nvidia not found is strange, as it works perfectly for opengl-only applications!

I also tried using nvidia-prime instead of bumblebee, with even less success.


Any help would be greatly appreciated.

---

