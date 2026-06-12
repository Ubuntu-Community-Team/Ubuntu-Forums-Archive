---
title: "GT640 wrong memory size?"
date: 2014-10-07
forum: Hardware
---

### Post by Roo8choo on 2014-10-07
Hello,

I have a Asus GT640 installed in my pc which has a Asus A88XM-A motherboard and I observed that my graphics card is taking memory from my RAM. I find that weird because my card supposed to have 2048MB video memory by itself? I'm using the Nvidia driver which is recommended in Ubuntu 14.04.

**Xorg.log:**
```

allard@ubuntu-pc-allard:~$ cat /var/log/Xorg.0.log | grep "virtual memory"
[     4.929] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory

```

**lscpi:**
```

allard@ubuntu-pc-allard:~$ sudo lspci -v -s 01:00.0
[sudo] password for allard: 
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 83f3
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia

```

**Xorg.log | grep NVIDIA:**
```
allard@ubuntu-pc-allard:~$ cat /var/log/Xorg.0.log | grep NVIDIA
[     4.211] (II) Module glx: vendor="NVIDIA Corporation"
[     4.211] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[     4.217] (II) Module nvidia: vendor="NVIDIA Corporation"
[     4.218] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[     4.218] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     4.224] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     4.224] (==) NVIDIA(0): RGB weight 888
[     4.224] (==) NVIDIA(0): Default visual is TrueColor
[     4.224] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     4.225] (**) NVIDIA(0): Option "NoLogo" "true"
[     4.225] (**) NVIDIA(0): Option "RegistryDwords" "PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
[     4.225] (**) NVIDIA(0): Enabling 2D acceleration
[     4.900] (II) NVIDIA(0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[     4.900] (II) NVIDIA(0):     3D Vision stereo.
[     4.900] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[     4.901] (II) NVIDIA(0): NVIDIA GPU GeForce GT 640 (GK107) at PCI:1:0:0 (GPU-0)
[     4.901] (--) NVIDIA(0): Memory: 2097152 kBytes
[     4.901] (--) NVIDIA(0): VideoBIOS: 80.07.26.00.26
[     4.901] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     4.903] (--) NVIDIA(0): Valid display device(s) on GeForce GT 640 at PCI:1:0:0
[     4.903] (--) NVIDIA(0):     CRT-0
[     4.903] (--) NVIDIA(0):     DFP-0
[     4.903] (--) NVIDIA(0):     DFP-1
[     4.903] (--) NVIDIA(0):     Samsung SyncMaster (DFP-2) (boot, connected)
[     4.903] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     4.903] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[     4.903] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[     4.903] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[     4.903] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[     4.903] (--) NVIDIA(0): Samsung SyncMaster (DFP-2): Internal Dual Link TMDS
[     4.903] (--) NVIDIA(0): Samsung SyncMaster (DFP-2): 330.0 MHz maximum pixel clock
[     4.903] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.903] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-2) (Using EDID frequencies
[     4.903] (**) NVIDIA(0):     has been enabled on all display devices.)
[     4.903] (WW) NVIDIA(GPU-0): The EDID for Samsung SyncMaster (DFP-2) contradicts itself:
[     4.903] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[     4.903] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[     4.903] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     4.903] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[     4.903] (WW) NVIDIA(GPU-0): The EDID for Samsung SyncMaster (DFP-2) contradicts itself:
[     4.903] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[     4.903] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[     4.903] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     4.903] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[     4.903] (WW) NVIDIA(GPU-0): The EDID for Samsung SyncMaster (DFP-2) contradicts itself:
[     4.903] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[     4.903] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[     4.903] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[     4.903] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[     4.904] (WW) NVIDIA(0): No valid modes for "DFP-2:1920x1080_60.00"; removing.
[     4.904] (WW) NVIDIA(0): 
[     4.904] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[     4.904] (WW) NVIDIA(0):     "nvidia-auto-select".
[     4.904] (WW) NVIDIA(0): 
[     4.904] (II) NVIDIA(0): Validated MetaModes:
[     4.904] (II) NVIDIA(0):     "DFP-2:nvidia-auto-select"
[     4.904] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     4.929] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[     4.929] (--) NVIDIA(0):     option
[     4.929] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     4.929] (II) NVIDIA:     access.
[     4.932] (II) NVIDIA(0): Setting mode "DFP-2:nvidia-auto-select"
[     4.974] (==) NVIDIA(0): Disabling shared memory pixmaps
[     4.974] (==) NVIDIA(0): Backing store enabled
[     4.974] (==) NVIDIA(0): Silken mouse enabled
[     4.975] (**) NVIDIA(0): DPMS enabled
[     4.976] (II) NVIDIA(0): [DRI2] Setup complete
[     4.976] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     6.159] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[     6.159] (II) NVIDIA(GPU-0):     3D Vision stereo.
[     6.388] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[     6.388] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    12.752] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[    12.752] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    13.207] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[    13.207] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    13.686] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[    13.686] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    14.089] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[    14.089] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    29.239] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-2)) does not support NVIDIA
[    29.239] (II) NVIDIA(GPU-0):     3D Vision stereo.

```

**free -m:**
```

allard@ubuntu-pc-allard:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         15921       1560      14361         11         53        598
-/+ buffers/cache:        909      15012
Swap:         1951          0       1951

```

What's going on here?

---

### Post by Michael_McKenney on 2014-10-07
In 64 bit Windows, the video cards would address ram above 16GB mark.  It was not using physical or virtual ram.  It was remapping into memory region.  Most computers never had over 4GB of RAM.  So it did not matter that this address range was used.  It was just to interact with the OS.  So it is taking 3GB of memory space to remap for transferring with the OS.

---

### Post by Roo8choo on 2014-10-07
> **Michael_McKenney said:**
> In 64 bit Windows, the video cards would address ram above 16GB mark.  It was not using physical or virtual ram.  It was remapping into memory region.  Most computers never had over 4GB of RAM.  So it did not matter that this address range was used.  It was just to interact with the OS.  So it is taking 3GB of memory space to remap for transferring with the OS.
Thanks for the reply. In other words, this is normal?

Is it also normal that Ubuntu shows 15921 (15.5GB) of RAM? In my BIOS it says 16384 (16GB). I'm using a AMD A8-5600K CPU so it could be that some RAM is taken away by the APU graphics.

---

