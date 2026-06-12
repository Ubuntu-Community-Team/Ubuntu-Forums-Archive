---
title: "Switching to dedicated AMD graphics"
date: 2018-05-29
forum: Hardware
---

### Post by ayala-adrian on 2018-05-29
Hi everyone,

I have a HP Envy 15 3040nr which came with the Radeon HD 7690M. I am running Ubuntu 18.04 currently. 
I would love to play the various games in my Steam library such as Stellaris (runs a bit okay but Main Menu graphics look weird), EVE Online runs a bit sluggish if I run two clients.

Is there anyone with any experience with this can assist me?

Thanks

Adrian


My BIOS is set to 'Fixed Mode' for Switchable Graphics

From the system details it displays "Intel Sandybridge Mobile" 

From Steam System Information (shorten for brevity)
```
Video Card:
    Driver:  Intel Open Source Technology Center Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
    Driver Version:  3.0 Mesa 18.0.0-rc5
    OpenGL Version: 3.0

```
```
ari@envy:~$ sudo lshw -c video
[sudo] password for ari: 
  *-display                 
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff


```


```
ari@envy:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741] (rev ff)

```

```
ari@envy:~$ dmesg | egrep "radeon|drm"
[    3.529179] [drm] radeon kernel modesetting enabled.
[    3.529427] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    3.529592] [drm] initializing kernel modesetting (TURKS 0x1002:0x6741 0x103C:0x1688 0x00).
[    3.530031] [drm] Memory usable by graphics device = 2048M
[    3.530032] [drm] Replacing VGA console driver
[    3.562090] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.562091] [drm] Driver supports precise vblank timestamp query.
[    3.604707] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    3.604708] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    3.604712] [drm] Detected VRAM RAM=1024M, BAR=256M
[    3.604713] [drm] RAM width 128bits DDR
[    3.604815] [drm] radeon: 1024M of VRAM memory ready
[    3.604816] [drm] radeon: 1024M of GTT memory ready.
[    3.604825] [drm] Loading TURKS Microcode
[    3.604896] [drm] Internal thermal controller without fan control
[    3.604903] radeon 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[    3.609803] [drm] radeon: dpm initialized
[    3.609862] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    3.610396] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    3.614944] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[    3.615061] radeon 0000:01:00.0: WB enabled
[    3.615063] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x0000000071f5172b
[    3.615065] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000d6af2a7b
[    3.615915] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x000000008383d872
[    3.615917] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.615917] [drm] Driver supports precise vblank timestamp query.
[    3.615918] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    3.616010] radeon 0000:01:00.0: radeon: using MSI.
[    3.616146] [drm] radeon: irq initialized.
[    3.632718] [drm] ring test on 0 succeeded in 2 usecs
[    3.632742] [drm] ring test on 3 succeeded in 20 usecs
[    3.643818] [drm] LVDS was detected, not registering eDP
[    3.808540] [drm] ring test on 5 succeeded in 2 usecs
[    3.808555] [drm] UVD initialized successfully.
[    3.808930] [drm] ib test on ring 0 succeeded in 0 usecs
[    3.809099] [drm] ib test on ring 3 succeeded in 0 usecs
[    4.476155] [drm] ib test on ring 5 succeeded
[    4.482770] [drm] Radeon Display Connectors
[    4.495027] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
[    4.495610] [drm] Initialized i915 1.6.0 20171023 for 0000:00:02.0 on minor 1
[    4.639164] fbcon: inteldrmfb (fb0) is primary device
[    5.542861] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   27.909091] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   27.915102] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[   27.915203] radeon 0000:01:00.0: WB enabled
[   27.915206] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x0000000071f5172b
[   27.915207] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000d6af2a7b
[   27.916021] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x000000008383d872
[   27.932349] [drm] ring test on 0 succeeded in 2 usecs
[   27.932374] [drm] ring test on 3 succeeded in 20 usecs
[   28.108150] [drm] ring test on 5 succeeded in 2 usecs
[   28.108164] [drm] UVD initialized successfully.
[   28.108367] [drm] ib test on ring 0 succeeded in 0 usecs
[   28.108553] [drm] ib test on ring 3 succeeded in 0 usecs
[   28.764240] [drm] ib test on ring 5 succeeded
[   42.731308] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   42.737286] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[   42.737384] radeon 0000:01:00.0: WB enabled
[   42.737387] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x0000000071f5172b
[   42.737389] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000d6af2a7b
[   42.738184] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x000000008383d872
[   42.754510] [drm] ring test on 0 succeeded in 2 usecs
[   42.754535] [drm] ring test on 3 succeeded in 20 usecs
[   42.930305] [drm] ring test on 5 succeeded in 2 usecs
[   42.930313] [drm] UVD initialized successfully.
[   42.930498] [drm] ib test on ring 0 succeeded in 0 usecs
[   42.930681] [drm] ib test on ring 3 succeeded in 0 usecs
[   43.612178] [drm] ib test on ring 5 succeeded
[   71.858957] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   71.865037] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[   71.865135] radeon 0000:01:00.0: WB enabled
[   71.865138] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x0000000071f5172b
[   71.865139] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000d6af2a7b
[   71.865934] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x000000008383d872
[   71.882364] [drm] ring test on 0 succeeded in 2 usecs
[   71.882389] [drm] ring test on 3 succeeded in 20 usecs
[   72.058159] [drm] ring test on 5 succeeded in 2 usecs
[   72.058174] [drm] UVD initialized successfully.
[   72.058368] [drm] ib test on ring 0 succeeded in 0 usecs
[   72.058556] [drm] ib test on ring 3 succeeded in 0 usecs
[   72.732295] [drm] ib test on ring 5 succeeded
```

---

### Post by Autodave on 2018-05-29
This is a decent laptop, but not really for gaming.  What resolution are you running the screen at when playing games? Native is 1,920 x 1,080. I would try lowering the resolution. Do it a little at a time, try game, see what you can live with.  If your game will display frame rates, watch that at different resolutions. The lower the resolution, the faster the frame rates and thus, better game play (smoother graphics). I would try for an absolute minimum of about 20FPS.

---

### Post by Yellow Pasque on 2018-05-29
You should be able to use DRI_PRIME like:
```
xrandr --listproviders
DRI_PRIME=1 glxinfo -B
```

---

### Post by ayala-adrian on 2018-05-29
Not sure what either of these commands do but I tried.
I ran both commands and the following is what was provided.


ari@envy:~$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x6d cap: 0x9, Source Output, Sink Offload crtcs: 2 outputs: 6 associated providers: 1 name:modesetting
Provider 1: id: 0x45 cap: 0x6, Sink Output, Source Offload crtcs: 6 outputs: 0 associated providers: 1 name:TURKS @ pci:0000:01:00.0
ari@envy:~$ man xrandr
ari@envy:~$ DRI_PRIME=1 glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: AMD TURKS (DRM 2.50.0 / 4.15.0-22-generic, LLVM 6.0.0) (0x6741)
    Version: 18.0.0
    Accelerated: yes
    Video memory: 1024MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 1023 MB, largest block: 1023 MB
    VBO free aux. memory - total: 1020 MB, largest block: 1020 MB
    Texture free memory - total: 1023 MB, largest block: 1023 MB
    Texture free aux. memory - total: 1020 MB, largest block: 1020 MB
    Renderbuffer free memory - total: 1023 MB, largest block: 1023 MB
    Renderbuffer free aux. memory - total: 1020 MB, largest block: 1020 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 1024 MB
    Total available memory: 2045 MB
    Currently available dedicated video memory: 1023 MB
OpenGL vendor string: X.Org
OpenGL renderer string: AMD TURKS (DRM 2.50.0 / 4.15.0-22-generic, LLVM 6.0.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.0.0-rc5
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.0 Mesa 18.0.0-rc5
OpenGL shading language version string: 1.30
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.0.0-rc5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10

---

### Post by ayala-adrian on 2018-05-29
It is a decent laptop for the games I played when it had Windows on it.
It isn't a framerate issue that I am experiencing but more like I am not even sure if gpu is being utilized. I posted this over in the reddit/r/linux_gaming and was shown that I can do the following:

Steam - Library - Right click to desired game - Properties- Launch Options 

  DRI_PRIME=1 %command%

This worked for Stellaris, but I should not have to insert this command for every game right?

---

### Post by Yellow Pasque on 2018-05-29
> Not sure what either of these commands do 
They weren't supposed to do anything other than print diagnostic output to confirm that DRI_PRIME works and selects the dedicated GPU (and it does).

> This worked for Stellaris, but I should not have to insert this command for every game right? 
Yes, you have to manually specify that you want to use the AMD GPU. There is no automatic detection/switching on Linux.
You can edit your launchers or use scripts/aliases to avoid typing DRI_PRIME=1 every time.

---

