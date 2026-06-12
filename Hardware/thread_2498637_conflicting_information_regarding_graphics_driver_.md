---
title: "conflicting information regarding graphics driver in use?"
date: 2024-06-22
forum: Hardware
---

### Post by csae2608 on 2024-06-22
Hello , 

i have an Laptop running Ubuntu 20.04 and it has dual graphics (i620 HD intel / Radeon RX 550X)

have installed amdgpu driver via amdgpu-install pacckage provided by AMD, but have to admit that this method is tricky and hope AMD could make it easier more foolproof in coming iterations;


now with amdgpu installed, i am getting conflicting information on which graphics driver used, or maybe i am just not familiar - not understanding on how Ubuntu handles the graphics side;

Under System it states

```
Graphics : llvmpipe (LLVM 15.0.3, 256bits / llvmpipe  (LLVM 15.0.3 , 256 bits
```

however another section has that "amdgpu" is in use as kernel

```
lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake) (rev 02)
    Subsystem: Lenovo UHD Graphics 620 (Whiskey Lake)
    Kernel driver in use: i915
    Kernel modules: i915
--
03:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] (rev c0)
    Subsystem: Lenovo Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu


```

glxinfo says

```
glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:

```

```
 glxinfo | grep -i opengl
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 15.0.3, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 22.3.0-devel
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5 (Compatibility Profile) Mesa 22.3.0-devel
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.3.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:


```

and
```
DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: llvmpipe (LLVM 15.0.3, 256 bits)
rich@rich-ThinkPad-E590:~/Programs/Geekbench-6.3.0-Linux$ DRI_PRIME=0 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: llvmpipe (LLVM 15.0.3, 256 bits)

```


so i am wondering if it states "kernel in use" "amdgpu" why then is "llvmpipe" shown as "opencl" renderer if i have installed the legacy drivers from AMD for the RX 550X?

also geekbench seem to suggest that i have AMDGPU for opencl and vulkan active;


clearly some conficting info here, or maybe i have just a botched installation of amdgpu running?


thanks for any help offered!

---

### Post by Yellow Pasque on 2024-06-22
> **csae2608 said:**
> Under System it states (llvmpipe)...however another section has that "amdgpu" is in use as kernel

Apples and oranges. One is the kernel module and one is the 3D driver. They are not conflicting. You are using both of them.

> have installed amdgpu driver via amdgpu-install package
Why? This is almost certainly how you screwed up your 3D and now see llvmpipe when you should see Intel <something> when you check glxinfo (or AMD <something> with DRI_PRIME=1)
Exactly what command did you use and what version of the installer did you use?

---

### Post by csae2608 on 2024-06-23
> **Yellow Pasque said:**
> Apples and oranges. One is the kernel module and one is the 3D driver. They are not conflicting. You are using both of them.


Why? This is almost certainly how you screwed up your 3D and now see llvmpipe when you should see Intel <something> when you check glxinfo (or AMD <something> with DRI_PRIME=1)
Exactly what command did you use and what version of the installer did you use?

Thanks, i did use the official driver package from AMD from their website for the RX 550X mobile graphics card (Polaris based).


The install was probably faulty, i should have use "usecase=workstation" instead i used "usecase=graphics" but that is just guessing;

in any case had the install via

```
sudo amdgpu-install --usecase=graphics --opencl=legacy --vulkan=amdvlk,pro --no-32 --accept-eula -y
```

but something must not have been ideal;

now i have upgraded to 22.04 and uninstall amdgpu for the moment and using the open source radeon drivers, too see if i might fare better.

---

### Post by csae2608 on 2024-06-23
now i am on 22.04 using Wayland and under "System" "about" it give this info

```
AMD® Radeon 500 series / Mesa Intel® UHD Graphics 620 (WHL GT2)
```


```
 lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation WhiskeyLake-U GT2 [UHD Graphics 620] (rev 02)
    Subsystem: Lenovo WhiskeyLake-U GT2 [UHD Graphics 620]
    Kernel driver in use: i915
    Kernel modules: i915
--
03:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] (rev c0)
    Subsystem: Lenovo Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```

```
 glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:

Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel (0x8086)
    Device: Mesa Intel(R) UHD Graphics 620 (WHL GT2) (0x3ea0)
    Version: 23.2.1
    Accelerated: yes
    Video memory: 15699MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) UHD Graphics 620 (WHL GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:

```

it seems Intel HD 620 is used for OpenGl i don§t know how the computer handles this which graphics chip is used for which task and who decides which one is used and for what purpoeses;

when i use "glxgears" i now get a much higher framerate than previously with "amdgpu-install" proprietary drivers, maybe trice the framerate, but that could also be because the installation could have gone wrong or as you stated was botched (the rx 550x should certainly be more capable than the HD 620 igpu)

```
glxinfo | grep -i opengl
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) UHD Graphics 620 (WHL GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 23.2.1-1ubuntu3.1~22.04.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

```

```
DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: AMD Radeon 500 Series (polaris12, LLVM 15.0.7, DRM 3.56, 6.5.0-41-generic)
DRI_PRIME=0 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa Intel(R) UHD Graphics 620 (WHL GT2)

```

geekbench however shows Vulkan properly installed and no OpenCL (which is proper since OpenCL could only be provided via amdgpu(legacy option) if i am not mistaken)

```
Vulkan
0 0 Intel(R) UHD Graphics 620 (WHL GT2)
0 1 AMD Radeon 500 Series (RADV POLARIS12)
0 2 llvmpipe (LLVM 15.0.7, 256 bits)

```

---

### Post by csae2608 on 2024-06-23
for glxgears results

Radeon rX 550X

```

DRI_PRIME=1 vblank_mode=0 glxgears
ATTENTION: default value of option vblank_mode overridden by environment.
19909 frames in 5.0 seconds = 3981.748 FPS
20058 frames in 5.0 seconds = 4011.562 FPS
19816 frames in 5.0 seconds = 3962.332 FPS
19635 frames in 5.0 seconds = 3926.933 FPS
X connection to :0 broken (explicit kill or server shutdown).



```

vs Intel HD 620

```

DRI_PRIME=0 vblank_mode=0 glxgears
ATTENTION: default value of option vblank_mode overridden by environment.
40237 frames in 5.0 seconds = 8047.274 FPS
41071 frames in 5.0 seconds = 8214.133 FPS
40091 frames in 5.0 seconds = 8018.044 FPS



```

---

### Post by Yellow Pasque on 2024-06-23
That all looks fine. For OpenCL, you may want to try Rusticl:
```
DRI_PRIME=1 RUSTICL_ENABLE=radeonsi clinfo --list
```

---

### Post by csae2608 on 2024-06-29
hello , it looked fine,

but some feature are missing , could not run this program here [https://www.svp-team.com/](https://www.svp-team.com/) with accelleration for frame interpolation

so ended up installing amdgpu in two steps (installing newer .deb package from amd resultet in amdgpu-install complaining about missing packages; so i ended up installing version 5.4.1 of amdgpu-install first [https://community.amd.com/t5/drivers-software/unable-to-install-amdgpu-pro-drivers-after-updating-ubuntu-22-04/td-p/575841](https://community.amd.com/t5/drivers-software/unable-to-install-amdgpu-pro-drivers-after-updating-ubuntu-22-04/td-p/575841) and then since this .deb would pull the correct files but not build for recent kernel, afterwards update the .deb file with recent one from amd for RX 550X graphics card) and now it seems video acceleration is functioning?

```
glxinfo

Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: Radeon 500 Series (polaris12, LLVM 17.0.4, DRM 3.56, 6.5.0-41-generic) (0x699f)

```

```
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: Radeon 500 Series (polaris12, LLVM 17.0.4, DRM 3.56, 6.5.0-41-generic) (0x699f)
    Version: 23.3.0
    Accelerated: yes
    Video memory: 2048MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2


```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293923&stc=1[/IMG]

---

