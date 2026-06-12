---
title: "PNY Quadro 6000 and Ubuntu 11.10"
date: 2012-05-07
forum: Hardware
---

### Post by PityOnU on 2012-05-07
Hi all,

I'm having some serious difficulty getting the nVidia CUDA drivers (from here: [http://developer.nvidia.com/cuda-downloads](http://developer.nvidia.com/cuda-downloads)) to play nice with my Ubuntu 11.10 x86_64 installation. The drivers for the card seem to randomly crash, first causing the screen to be covered in little blue and yellow transparent squares for about 5 seconds before just crashing out of X into a terminal. Here is the error message in syslog after droppping out:

```

[ 1738.392321] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1738.392767] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1738.416067] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1738.416507] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1738.575493] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1738.575931] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1738.687254] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1738.687692] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1742.088145] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1742.088588] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1742.167887] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1742.168330] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1743.768222] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1743.768665] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1743.888014] NVRM: Xid (0000:05:00): 56, CMDre 00000000 0000089c 0100cb1a 00000007 00000000
[ 1743.888454] NVRM: Xid (0000:05:00): 56, CMDre 00000000 00000c9c 0100cb1a 00000007 00000000
[ 1758.669294] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1758.669307] NVRM: rm_init_adapter(0) failed
[ 1760.270078] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1760.270091] NVRM: rm_init_adapter(0) failed
[ 1761.857999] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1761.858014] NVRM: rm_init_adapter(0) failed
[ 1763.443884] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1763.443896] NVRM: rm_init_adapter(0) failed
[ 1765.036627] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1765.036639] NVRM: rm_init_adapter(0) failed
[ 1766.601768] NVRM: RmInitAdapter failed! (0x27:0xffffffff:1190)
[ 1766.601780] NVRM: rm_init_adapter(0) failed

```

And here is some more information from the X server log:

```

[   105.656] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   105.656] (==) NVIDIA(0): RGB weight 888
[   105.656] (==) NVIDIA(0): Default visual is TrueColor
[   105.656] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   105.656] (**) NVIDIA(0): Option "TwinView" "1"
[   105.656] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
[   105.656] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[   105.657] (**) NVIDIA(0): Enabling 2D acceleration
[   107.117] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:5:0:0.  Please
[   107.117] (EE) NVIDIA(0):     check your system's kernel log for additional error
[   107.117] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[   107.117] (EE) NVIDIA(0):     README for additional information.
[   107.117] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[   107.117] (II) UnloadModule: "nvidia"
[   107.117] (II) Unloading nvidia
[   107.117] (II) UnloadModule: "wfb"
[   107.117] (II) Unloading wfb
[   107.117] (II) UnloadModule: "fb"
[   107.117] (II) Unloading fb
[   107.117] (EE) Screen(s) found, but none have a usable configuration.

```

The system is using the Asus KGPE-D16 motherboard with two AMD Opteron 6220's installed and 64GB of DDR3-1333 ECC RDIMM. There is a PNY Quadro 6000 card installed, along with a Tesla C2075. The nouveau open source nVidia driver has been completely removed from the system, and GDM is the main display manager using the gnome-session-fallback desktop. Here is the output from 'uname -a'

```
Linux -------- 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

I have tried different kernels and different version of the nVidia driver, all to no avail. The card is rendered pretty much useless when it is this unstable, which is a damn shame as it is the top-of-the-line nVidia workstation card that cost about $4000.

I would really like to know:

1. Has anyone else has experienced this problem or something similar?
2. Does this sound like more of a software or hardware problem?
3. Any other general insights that you think may be useful.

Thank you all very much in advance!

---

### Post by PityOnU on 2012-05-08
Discovered the source of the problem.

Both the 64-bit nVidia CUDA developer driver version 295.41 and the 64-bit standard nVidia display driver version 302.07 are unstable and unusable on Linux machines when used with a PNY Quadro 6000 GPGPU. I tested these on Ubuntu 11.10 and 12.04 and CentOS 6.2. Using the 290.10 display driver fixed the issue and had everything running smooth once again. (This is compared to no problems at all with the latest drivers on Windows 7 64-bit.)

It disappoints me that nVidia's flagship workstation card, the one that costs huge amounts of money but supposedly guarantees reliability, stability, and long term support from the company, is essentially broken with the latest version of the drivers on Linux.

---

### Post by PityOnU on 2012-05-10
Turns out that this did not solve the problem - the older drivers did  increase the overall stability of the card but it still eventually  crashes out with that same error.

Any suggestions?

---

