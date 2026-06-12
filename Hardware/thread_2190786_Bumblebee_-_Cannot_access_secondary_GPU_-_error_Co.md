---
title: "Bumblebee - Cannot access secondary GPU - error: Could not load GPU driver"
date: 2013-11-29
forum: Hardware
---

### Post by Asheboy on 2013-11-29
Hi,

I am trying to get Bumblebee to run correcting on my ThinkPad T440s with a NVIDIA GeForce GT 730M. When I try to run applications I receive the following error:

```

asheboy@asheboy-ThinkPad-T440s:~$ optirun google-chrome
[ 9781.716274] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 9781.716357] [ERROR]Aborting because fallback start is disabled.

```

A more verbose output gives:

```
asheboy@asheboy-ThinkPad-T440s:~$ optirun -vvv google-chrome
[10042.718213] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[10042.718919] [INFO]Configured driver: nvidia
[10042.719218] [DEBUG]optirun version 3.2.1 starting...
[10042.719287] [DEBUG]Active configuration:
[10042.719367] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[10042.719433] [DEBUG] X display: :8
[10042.719508] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-304-updates:/usr/lib32/nvidia-304-updates
[10042.719585] [DEBUG] Socket path: /var/run/bumblebee.socket
[10042.719657] [DEBUG] Accel/display bridge: auto
[10042.719730] [DEBUG] VGL Compression: proxy
[10042.719802] [DEBUG] VGLrun extra options: 
[10042.719876] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[10042.720135] [DEBUG]Using auto-detected bridge primus
[10042.775896] [INFO]Response: No - error: Could not load GPU driver

[10042.775941] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[10042.775963] [DEBUG]Socket closed.
[10042.776062] [ERROR]Aborting because fallback start is disabled.
[10042.776086] [DEBUG]Killing all remaining processes.
```

My /etc/bumblebee/bumblebee.conf is as follows:

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
KernelDriver=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau


```


uname -a is:

```
asheboy@asheboy-ThinkPad-T440s:~$ uname -a
Linux asheboy-ThinkPad-T440s 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I am running Kubuntu 13.10.

Can anyone help me to get bumblebee to enable my gpu and run applications?

Thanks,

Ash

---

### Post by lucidlytwisted on 2013-12-01
I've been using Bumblebee on a T430 with the closed nvidia drivers. Looks like you are running the stock nivida driver and I assume you have bumblebee-nvidia installed (the usual nvidia install will break mesa).
Have you checked your nvidia xorg.conf? (Same folder as bumblebee.conf). Does it contain the PCIBUS information? If not, try adding that.

Make sure you have followed the steps [here]("http://wiki.ubuntu.com/Bumblebee") exactly. The Bumblee wiki contains more [troubleshooting information]("http://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting").

Be aware though that the performance under Bumblebee is still bit hit-and-miss. I am seeing about 1/4 the expected performance (half that of the IGP Intel HD 4000), I see others reporting much improved performance.

---

