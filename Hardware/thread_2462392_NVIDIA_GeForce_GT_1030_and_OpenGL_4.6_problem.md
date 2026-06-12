---
title: "NVIDIA GeForce GT 1030 and OpenGL 4.6 problem"
date: 2021-05-19
forum: Hardware
---

### Post by ewok002 on 2021-05-19
Hello
my conf:
ESXI 7.0 with the GeForce GT 1030 in pass-through to a VM Ubuntu
I have installed the lates driver : NVIDIA-SMI 465.31
 The GPU seems to works :
 
[LIST]
[*]nvidia-smi activity with a boinc task 
[*]glxgears works 
[/LIST]
 [B][SIZE=1][FONT=arial]
But  when I launch yuzu (game emulator application) I get a error message  link to OpenGL 4.6 not supported despite the fact that this card and  driver are 4.6 compatible…
[/FONT][/SIZE][/B]
[B][SIZE=1][FONT=arial] Your GPU may not support OpenGL 4.6, or you do not have the latest graphics driver.
GL Renderer:
llvmpipe (LLVM 11.0.0, 256 bits)[/FONT][/SIZE][/B]

 Any idea to investigate?

 What other application using openGL can I test to know if it is an yuzu error or OpenGl instalation?

Thanks

---

### Post by Yellow Pasque on 2021-05-19
To look at OpenGL system info:
```
glxinfo -B
```

---

### Post by ewok002 on 2021-05-19
> glxinfo -B
name of display: localhost:10.0
display: localhost:10  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa/X.org (0xffffffff)
    Device: llvmpipe (LLVM 11.0.0, 256 bits) (0xffffffff)
    Version: 20.2.6
    Accelerated: no
    Video memory: 3935MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 11.0.0, 256 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.2.6
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 3.1 Mesa 20.2.6
OpenGL shading language version string: 1.40
OpenGL context flags: (none)

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.2.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

Which number is the good one ?
4.5 or 3.2 or 3.1 or 1.1 ?

---

### Post by Yellow Pasque on 2021-05-19
Your Passthru is not working
```
OpenGL renderer string: llvmpipe (LLVM 11.0.0, 256 bits)
```
That's software/CPU acceleration.

I don't know anything about esxi, so I'm afraid I personally can't be much help except maybe you can file a bug, and maybe I'll see something in the logs it gathers.

---

### Post by ewok002 on 2021-05-19
MAybe not fully working :-) but working a litle...
When I do a "nvidia-smi" with calculation done by boinc I get
> +-----------------------------------------------------------------------------+
| NVIDIA-SMI 465.31       Driver Version: 465.31       CUDA Version: 11.3     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:03:00.0 Off |                  N/A |
| 44%   60C    P0    N/A /  30W |    114MiB /  2001MiB |     97%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1348      C   ...ux-gnu__opencl_nvidia_101      112MiB |
+-----------------------------------------------------------------------------+


---

### Post by ewok002 on 2021-05-24
It's strange..
The command : inxi -Gx
> Graphics:  Device-1: NVIDIA GP108 [GeForce GT 1030] vendor: Micro-Star MSI driver: nvidia v: 465.31 bus ID: 03:00.0 
           Display: server: X.Org 1.20.9 driver: nvidia tty: N/A 
           OpenGL: renderer: llvmpipe (LLVM 11.0.0 256 bits) v: 4.5 Mesa 20.2.6 direct render: Yes 

It's seem's that Ubuntu detect the card.
But the OpenGL driver link to the card is not loaded => OpenGL: renderer: llvmpipe (LLVM 11.0.0 256 bits)

Where can I find some information / configuration on the OpenGL driver to be loaded?

---

### Post by Yellow Pasque on 2021-05-24
Maybe look at dmesg or /var/log/Xorg.0.log (assuming you're not running in Wayland session).

---

### Post by ewok002 on 2021-05-24
I did nothing to install Wayland (but I am not familiar with Wayland...) 

In dmesg nothing with "opengl" keyword.
I have for "gpu" keyword
```
[    1.985336] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
```


and for "nviadia"
```
[    1.674968] nvidia: loading out-of-tree module taints kernel.
[    1.681407] nvidia: module license 'NVIDIA' taints kernel.
[    1.720068] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    1.737961] nvidia-nvlink: Nvlink Core is being initialized, major device number 240
[    1.752184] nvidia 0000:03:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    1.883186] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  460.73.01  Thu Apr  1 21:40:36 UTC 2021
[    1.931614] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  460.73.01  Thu Apr  1 21:32:31 UTC 2021
[    1.985336] [drm] [nvidia-drm] [GPU ID 0x00000300] Loading driver
[    1.992081] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:03:00.0 on minor 0
[    5.744558] nvidia-uvm: Loaded the UVM driver, major device number 237.
[    6.353229] audit: type=1400 audit(1621882678.530:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=814 comm="apparmor_parser"
[    6.353231] audit: type=1400 audit(1621882678.530:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=814 comm="apparmor_parser"
```

except "module verification failed" nothing seem's bad...

and in the Worg.0.log 
```

[    10.395] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[    10.403] (II) Applying OutputClass "nvidia" to /dev/dri/card0
[    10.404]     loading driver: nvidia
[    10.661] (==) Matched nvidia as autoconfigured driver 0
[    10.661] (II) LoadModule: "nvidia"
[    10.661] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[    10.667] (II) Module nvidia: vendor="NVIDIA Corporation"
[    10.671] (II) NVIDIA dlloader X Driver  460.73.01  Thu Apr  1 21:37:53 UTC 2021
[    10.671] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    10.671] (II) NOUVEAU driver for NVIDIA chipset families :
[    10.677] (II) NVIDIA(0): Creating default Display subsection in Screen section
[    10.677] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    10.677] (==) NVIDIA(0): RGB weight 888
[    10.677] (==) NVIDIA(0): Default visual is TrueColor
[    10.677] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.677] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[    10.677] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[    10.677] (**) NVIDIA(0): Enabling 2D acceleration
[    10.677] (II) Loading sub module "glxserver_nvidia"
[    10.677] (II) LoadModule: "glxserver_nvidia"
[    10.677] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglxserver_nvidia.so
[    10.712] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[    10.712] (II) NVIDIA GLX Module  460.73.01  Thu Apr  1 21:35:16 UTC 2021
[    10.713] (II) NVIDIA: The X server supports PRIME Render Offload.
[    11.241] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:3:0:0
[    11.241] (--) NVIDIA(0):     DFP-0
[    11.241] (--) NVIDIA(0):     DFP-1
[    11.241] (--) NVIDIA(0):     DFP-2
[    11.242] (II) NVIDIA(0): NVIDIA GPU GeForce GT 1030 (GP108-A) at PCI:3:0:0 (GPU-0)
[    11.242] (--) NVIDIA(0): Memory: 2097152 kBytes
[    11.242] (--) NVIDIA(0): VideoBIOS: 86.08.24.00.23
[    11.242] (II) NVIDIA(0): Detected PCI Express Link width: 4X
[    11.242] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    11.242] (--) NVIDIA(GPU-0): DFP-0: Internal DisplayPort
[    11.242] (--) NVIDIA(GPU-0): DFP-0: 1440.0 MHz maximum pixel clock
[    11.242] (--) NVIDIA(GPU-0): 
[    11.242] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    11.242] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    11.242] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    11.242] (--) NVIDIA(GPU-0): 
[    11.242] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    11.242] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    11.242] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    11.242] (--) NVIDIA(GPU-0): 
[    11.242] (==) NVIDIA(0): 
[    11.242] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    11.242] (==) NVIDIA(0):     will be used as the requested mode.
[    11.242] (==) NVIDIA(0): 
[    11.242] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[    11.242] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[    11.242] (II) NVIDIA(0): Validated MetaModes:
[    11.242] (II) NVIDIA(0):     "NULL"
[    11.242] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    11.242] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    11.242] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    11.243] (II) NVIDIA: Using 24576.00 MB of virtual memory for indirect memory
[    11.243] (II) NVIDIA:     access.
[    11.245] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    11.245] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    11.245] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    11.245] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    11.245] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    11.245] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    11.245] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    11.245] (II) NVIDIA(0):     Config Options in the README.
[    11.260] (II) NVIDIA(0): Setting mode "NULL"
[    11.266] (==) NVIDIA(0): Disabling shared memory pixmaps
[    11.266] (==) NVIDIA(0): Backing store enabled
[    11.266] (==) NVIDIA(0): Silken mouse enabled
[    11.267] (==) NVIDIA(0): DPMS enabled
[    11.268] (II) NVIDIA(0): [DRI2] Setup complete
[    11.268] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    11.728] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    11.728] (--) NVIDIA(GPU-0): DFP-0: Internal DisplayPort
[    11.728] (--) NVIDIA(GPU-0): DFP-0: 1440.0 MHz maximum pixel clock
[    11.728] (--) NVIDIA(GPU-0): 
[    11.728] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    11.728] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    11.728] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    11.728] (--) NVIDIA(GPU-0): 
[    11.728] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    11.728] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    11.728] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    11.728] (--) NVIDIA(GPU-0): 
```

maybe somting wrong with the 
```
[    11.245] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    11.245] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    11.245] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    11.245] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    11.245] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    11.245] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    11.245] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    11.245] (II) NVIDIA(0):     Config Options in the README.
```
?

in Xorg, nothing related to Opengl....

---

### Post by Yellow Pasque on 2021-05-24
Please use code tags for the copy/paste. It's difficult for me to skim logs with weird fonts. Better yet, file a bug on launchpad against xorg and it will gather all the logs for you.

---

### Post by ewok002 on 2021-05-24
Sorry, previous post modified

What do you mean by "Better yet, file a bug on launchpad against xorg and it will gather all the logs for you." ?

---

### Post by mastablasta on 2021-05-25
> **ewok002 said:**
> I did nothing to install Wayland (but I am not familiar with Wayland...) 


wayland is the new default in Ubuntu. wayland will replace the very old X.org and currently still lacks some features from what i've read. nvidia drivers do not work well with it because nvidia has not updated them yet.

so if you have nvidia card, you should select xorg at login unless you want to experiment with wayland. another option is to install a derivative like Kubuntu that still uses X.org.

---

### Post by ewok002 on 2021-05-25
When looking at the way to deactivate Wayland I am not sure it's applicable in my case.
I am on a Ubuntu server connected with ssh...

a "echo $XDG_SESSION_TYPE" gives "tty" and not Xorg or Wayland

---

### Post by ewok002 on 2021-05-25
On another forum I have seen a post where someone try the folowing command :
xrandr --listproviders

My answer is
Providers: number : 1
```
 Provider 0: id: 0x45 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 3 associated providers: 0 name:modesetting
```

he has the Graphic card in stead of "modesetting" ?

---

### Post by ewok002 on 2021-05-25
another thing that show the PCI card is well recognised by Ubuntu :

```
lspci -k

03:00.0 VGA compatible controller: NVIDIA Corporation GP108 [GeForce GT 1030] (rev a1)
    DeviceName: pciPassthru0
    Subsystem: Micro-Star International Co., Ltd. [MSI] GP108 [GeForce GT 1030]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```

---

### Post by Yellow Pasque on 2021-05-25
Maybe here: [https://medium.com/@davidramsay/setting-up-gtx-1070-passthrough-with-esxi-2c4f3519d39e](https://medium.com/@davidramsay/setting-up-gtx-1070-passthrough-with-esxi-2c4f3519d39e)
See the part about hypervisor cpuid.

---

### Post by ewok002 on 2021-05-26
Thanks for Help
I already has the hypervisor.cpuid.v0 = "FALSE"
 
But I try to install cuda with "nvidia-cuda-toolkit" as it seem's to be link to OpenGL but it does not change anythings...

When looking to discover what CUDA is I see something about "nvidia-settings" and it seem's there is a problem...

```
nvidia-settings

ERROR: Unable to load info from any available system

(nvidia-settings:5054): GLib-GObject-CRITICAL **: 18:57:49.721: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 18:57:49.723: PRIME: No offloading required. Abort
** Message: 18:57:49.723: PRIME: is it supported? no
```

---

### Post by mastablasta on 2021-05-26
nvidia-settings is a GUI application. if this is only server and all you have is CLI then i doubt it will work. though they may have parameters to use in CLI as well.

you could try asking on nvidia linux dev forums. they are quite helpful there and know a lot about this kind of stuff..

---

### Post by ewok002 on 2021-05-27
It's a server, but I have a ssh with export display.
I can open any application, from xclock, firefoxe, or even Blender...
But Blender witout OpenGL is very slow....

I have try to post on the nvidia linux forum. 
But after reading some post on this forum I have the feeling that teir problem is more on "nvidia-smi" not working or some difficulty on installing drivers.

My problem "I think" is "only" related to the OpenGl driver loading by Ubuntu. I suspect that the standard OpenGL library is loaded and not the one of Nvidia...
But I don't see any log error related to OpenGL...

---

