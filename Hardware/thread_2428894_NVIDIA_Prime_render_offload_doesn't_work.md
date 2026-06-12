---
title: "NVIDIA Prime render offload doesn't work"
date: 2019-10-10
forum: Hardware
---

### Post by Herudin on 2019-10-10
Hi everyone!
Nvidia [announced]("https://devtalk.nvidia.com/default/topic/1060977/announcements-and-news/-linux-solaris-and-freebsd-driver-435-17-beta-release-/") Vulkan and OpenGL+GLX support for prime render offload in proprietary driver since version 435.17
Basically it allows you to render screen on intel GPU but run some apps on nvidia GPU without switching cards and restarting Xserver. 

Now I'm trying to configure my laptop with Intel UHD 620 and Nvidia Geforce 1050 Max-Q to use this feature according to [official README guide]("http://download.nvidia.com/XFree86/Linux-x86_64/435.17/README/primerenderoffload.html").
On kubuntu 19.04 I've installed latest nvidia proprietary driver 435.21 and Xorg 1.20.4 with the necessary patches from [PPA]("https://launchpad.net/~aplattner/+archive/ubuntu/ppa/").
The driver installed correctly and I'm able to switch from iGPU to nvidia and vice versa with logout/login procedure, but render offload does not seem to work.

Here is what i get:
```
:~$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x44 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 2 associated providers: 0 name:modesetting
Provider 1: id: 0x1be cap: 0x0 crtcs: 0 outputs: 0 associated providers: 0 name:modesetting
```
Here "Provider 1" should have "name:NVIDIA-G0" not "modesetting"

```
:~$ __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia glxgears
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  25
  Current serial number in output stream:  26
```
This should return something about NVIDIA, I think.

Does anyone have same issue and any idea how to fix it?

[Here]("https://pastebin.com/zHji0WEz") is my xorg.conf
[Here]("https://pastebin.com/fvz3eSnM") is my Xorg.0.log

---

