---
title: "Second monitor not detected (18.04)"
date: 2020-01-12
forum: Hardware
---

### Post by lord-raiden2 on 2020-01-12
I have severe problems to use my dual monitor setup consisting of two Dell U2719D displays. I am connecting them via 2 Displayport cables directly to my Sapphire RX 5700XT Nitro. Only one of both monitors is recognized. The same happens if I connect one monitor via HDMI and the other via Displayport. The system is running on Kubuntu LTS with Kernel 5.0.0-37-generic.
Here the system information about the GPU:
```
$ lspci -vnn | grep VGA -A 12
1e:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] [1002:731f] (rev c1) (prog-if 00 [VGA controller])
    Subsystem: Sapphire Technology Limited Device [1da2:e409]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at e000 [size=256]
    Memory at fe400000 (32-bit, non-prefetchable) [size=512K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
```

I also updated the Mesa drivers via PPA:
```
$ glxinfo | grep 'version'
server glx version string: 1.4 client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL core profile version string: 3.3 (Core Profile) Mesa 19.1.2 - padoka PPA
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.1 Mesa 19.1.2 - padoka PPA
OpenGL shading language version string: 1.40
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 19.1.2 - padoka PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
```

I already had problems to change the resolution in the beginning, as it was stuck to 1024x768. Changing the resolution via xrandr was not possible as I only got the following output:
```
$ xrandr
xrandr: Failed to get size of gamma for output default
```

 I had to add the following line in /etc/default/grub to get native WQHD resolution:
```
GRUB_GFXMODE=2560x1440
```

After this modification I get the following output for xrandr command:
```
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 2560 x 1440, current 2560 x 1440, maximum 2560 x 1440
default connected primary 2560x1440+0+0 0mm x 0mm
2560x1440     93.00* 
```

The system is working fine on my Windows 10 gaming partition, so it should not be faulty hardware or cables. Is there a chance to resolve this issue or can I forget about that?

---

### Post by mörgæs on 2020-01-12
Hi, welcome to the fora.

With a graphics card this new 18.04 is not necessarily a good choice, even with a PPA added. I suggest that you try a clean install of 20.04 though it's still in development.

---

### Post by kurt18947 on 2020-01-12
I had trouble with 2 monitors with 18.04. I installed 18.04 HWE (installs current kernel & X.org) and now it works. This is using onboard video from Ryzen 3 2200G. It also worked without modificaion running a 19.10 live USB. I downloaded a daily of 20.04. It loaded but the mouse pointer was frozen.

---

### Post by lord-raiden2 on 2020-01-13
That's a real bummer. But thank you for the fast reply. I have installed the 18.04 HWE, but that didn't help.
I guess I will install an old NVidia NVS295 and check if that works. I will give a short update how that works out.

---

### Post by mörgæs on 2020-01-13
I guess it would be easier to do software than hardware experiments but yes, please post the results.

---

### Post by lord-raiden2 on 2020-01-14
The second GPU did not really help, so instead I switched to Manjaro with Kernel 5.4.6-2. Everything worked out of the box. No xrandr problems, native WQHD resolution and recognition of second monitor in daisy chain as well as directly connected to GPU.
Thank you for your help.

---

