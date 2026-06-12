---
title: "Black screen on resume from suspend (HP Pavilion g7)"
date: 2014-10-17
forum: Hardware
---

### Post by qwikrazor87 on 2014-10-17
Hello everyone.
I just got an HP Pavilion g7 (bought used from Amazon) which came installed with Windows 7 Home Premium.
It has a 500 GB HDD, 4 GB RAM and 4 core CPU.
I did a clean install of Ubuntu 12.04.5 LTS (desktop 64 bit).
I checked for any candidates of proprietary drivers but no matches were found.

The issue I'm having is when I put the laptop into suspend mode and then resume it, the screen just stays black but things are still running in the background.
Here is some info, if more is needed let me know.
```
qwikrazor87@linux:~/Desktop$ cat /proc/meminfo
MemTotal:        3508924 kB
MemFree:         1898084 kB
Buffers:          160660 kB
Cached:           622048 kB
SwapCached:            0 kB
Active:           992620 kB
Inactive:         408304 kB
Active(anon):     618980 kB
Inactive(anon):      300 kB
Active(file):     373640 kB
Inactive(file):   408004 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       3645436 kB
SwapFree:        3645436 kB
Dirty:                56 kB
Writeback:             0 kB
AnonPages:        618296 kB
Mapped:           126676 kB
Shmem:              1068 kB
Slab:             115624 kB
SReclaimable:      90796 kB
SUnreclaim:        24828 kB
KernelStack:        3176 kB
PageTables:        24072 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5399896 kB
Committed_AS:    2501608 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       94780 kB
VmallocChunk:   34359637416 kB
HardwareCorrupted:     0 kB
AnonHugePages:    180224 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       81704 kB
DirectMap2M:     2516992 kB
DirectMap1G:     1048576 kB
```
```
qwikrazor87@linux:~/Desktop$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.47
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.47
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.47
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.47
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb
```

Edit:
Updated with graphics info:
```
qwikrazor87@linux:~/Desktop$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: BeaverCreek [Radeon HD 6520G]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f033ffff
```

Edit2:
Here's the output from the xorg log:
```
[    24.375] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    24.375] X Protocol Version 11, Revision 0
[    24.375] Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
[    24.375] Current Operating System: Linux linux 3.13.0-37-generic #64~precise1-Ubuntu SMP Wed Sep 24 21:37:11 UTC 2014 x86_64
[    24.375] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=68e40670-2e88-4342-8687-2413678f0752 ro quiet splash vt.handoff=7
[    24.375] Build Date: 07 August 2014  11:49:36AM
[    24.375] xorg-server 2:1.15.1-0ubuntu2~precise2 (For technical support please see http://www.ubuntu.com/support) 
[    24.375] Current version of pixman: 0.30.2
[    24.375]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.375] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.375] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 17 19:44:04 2014
[    24.477] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.511] (==) No Layout section.  Using the first Screen section.
[    24.511] (==) No screen section available. Using defaults.
[    24.511] (**) |-->Screen "Default Screen Section" (0)
[    24.511] (**) |   |-->Monitor "<default monitor>"
[    24.532] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.532] (==) Automatically adding devices
[    24.532] (==) Automatically enabling devices
[    24.532] (==) Automatically adding GPU devices
[    24.606] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.606]     Entry deleted from font path.
[    24.606] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.606]     Entry deleted from font path.
[    24.606] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.606]     Entry deleted from font path.
[    24.608] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.608]     Entry deleted from font path.
[    24.608] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.608]     Entry deleted from font path.
[    24.608] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.608] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.608] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.608] (II) Loader magic: 0x7fbab3293c20
[    24.608] (II) Module ABI versions:
[    24.608]     X.Org ANSI C Emulation: 0.4
[    24.608]     X.Org Video Driver: 15.0
[    24.608]     X.Org XInput driver : 20.0
[    24.608]     X.Org Server Extension : 8.0
[    24.609] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.610] (--) PCI:*(0:0:1:0) 1002:9647:103c:3568 rev 0, Mem @ 0xe0000000/268435456, 0xf0300000/262144, I/O @ 0x00003000/256
[    24.626] Initializing built-in extension Generic Event Extension
[    24.626] Initializing built-in extension SHAPE
[    24.626] Initializing built-in extension MIT-SHM
[    24.626] Initializing built-in extension XInputExtension
[    24.626] Initializing built-in extension XTEST
[    24.626] Initializing built-in extension BIG-REQUESTS
[    24.626] Initializing built-in extension SYNC
[    24.626] Initializing built-in extension XKEYBOARD
[    24.626] Initializing built-in extension XC-MISC
[    24.626] Initializing built-in extension SECURITY
[    24.626] Initializing built-in extension XINERAMA
[    24.626] Initializing built-in extension XFIXES
[    24.626] Initializing built-in extension RENDER
[    24.626] Initializing built-in extension RANDR
[    24.626] Initializing built-in extension COMPOSITE
[    24.626] Initializing built-in extension DAMAGE
[    24.626] Initializing built-in extension MIT-SCREEN-SAVER
[    24.626] Initializing built-in extension DOUBLE-BUFFER
[    24.626] Initializing built-in extension RECORD
[    24.626] Initializing built-in extension DPMS
[    24.626] Initializing built-in extension X-Resource
[    24.626] Initializing built-in extension XVideo
[    24.626] Initializing built-in extension XVideo-MotionCompensation
[    24.626] Initializing built-in extension XFree86-VidModeExtension
[    24.626] Initializing built-in extension XFree86-DGA
[    24.626] Initializing built-in extension XFree86-DRI
[    24.626] Initializing built-in extension DRI2
[    24.626] (II) LoadModule: "glx"
[    24.726] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.255] (II) Module glx: vendor="X.Org Foundation"
[    25.255]     compiled for 1.15.1, module version = 1.0.0
[    25.255]     ABI class: X.Org Server Extension, version 8.0
[    25.255] (==) AIGLX enabled
[    25.255] Loading extension GLX
[    25.255] (==) Matched fglrx as autoconfigured driver 0
[    25.255] (==) Matched ati as autoconfigured driver 1
[    25.255] (==) Matched fglrx as autoconfigured driver 2
[    25.255] (==) Matched ati as autoconfigured driver 3
[    25.256] (==) Matched modesetting as autoconfigured driver 4
[    25.256] (==) Matched fbdev as autoconfigured driver 5
[    25.256] (==) Matched vesa as autoconfigured driver 6
[    25.256] (==) Assigned the driver to the xf86ConfigLayout
[    25.256] (II) LoadModule: "fglrx"
[    25.256] (WW) Warning, couldn't open module fglrx
[    25.256] (II) UnloadModule: "fglrx"
[    25.256] (II) Unloading fglrx
[    25.256] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    25.256] (II) LoadModule: "ati"
[    25.256] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    25.298] (II) Module ati: vendor="X.Org Foundation"
[    25.298]     compiled for 1.15.1, module version = 7.3.0
[    25.298]     Module class: X.Org Video Driver
[    25.298]     ABI class: X.Org Video Driver, version 15.0
[    25.299] (II) LoadModule: "radeon"
[    25.299] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    25.553] (II) Module radeon: vendor="X.Org Foundation"
[    25.554]     compiled for 1.15.1, module version = 7.3.0
[    25.554]     Module class: X.Org Video Driver
[    25.554]     ABI class: X.Org Video Driver, version 15.0
[    25.554] (II) LoadModule: "modesetting"
[    25.554] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.613] (II) Module modesetting: vendor="X.Org Foundation"
[    25.614]     compiled for 1.15.1, module version = 0.8.1
[    25.614]     Module class: X.Org Video Driver
[    25.614]     ABI class: X.Org Video Driver, version 15.0
[    25.614] (II) LoadModule: "fbdev"
[    25.614] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.655] (II) Module fbdev: vendor="X.Org Foundation"
[    25.655]     compiled for 1.15.1, module version = 0.4.4
[    25.655]     Module class: X.Org Video Driver
[    25.655]     ABI class: X.Org Video Driver, version 15.0
[    25.655] (II) LoadModule: "vesa"
[    25.655] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.673] (II) Module vesa: vendor="X.Org Foundation"
[    25.673]     compiled for 1.15.1, module version = 2.3.3
[    25.673]     Module class: X.Org Video Driver
[    25.673]     ABI class: X.Org Video Driver, version 15.0
[    25.673] (==) Matched fglrx as autoconfigured driver 0
[    25.673] (==) Matched ati as autoconfigured driver 1
[    25.673] (==) Matched fglrx as autoconfigured driver 2
[    25.673] (==) Matched ati as autoconfigured driver 3
[    25.673] (==) Matched modesetting as autoconfigured driver 4
[    25.673] (==) Matched fbdev as autoconfigured driver 5
[    25.673] (==) Matched vesa as autoconfigured driver 6
[    25.673] (==) Assigned the driver to the xf86ConfigLayout
[    25.673] (II) LoadModule: "fglrx"
[    25.673] (WW) Warning, couldn't open module fglrx
[    25.673] (II) UnloadModule: "fglrx"
[    25.673] (II) Unloading fglrx
[    25.673] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    25.673] (II) LoadModule: "ati"
[    25.673] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    25.673] (II) Module ati: vendor="X.Org Foundation"
[    25.673]     compiled for 1.15.1, module version = 7.3.0
[    25.673]     Module class: X.Org Video Driver
[    25.673]     ABI class: X.Org Video Driver, version 15.0
[    25.673] (II) LoadModule: "modesetting"
[    25.673] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.673] (II) Module modesetting: vendor="X.Org Foundation"
[    25.673]     compiled for 1.15.1, module version = 0.8.1
[    25.673]     Module class: X.Org Video Driver
[    25.673]     ABI class: X.Org Video Driver, version 15.0
[    25.673] (II) UnloadModule: "modesetting"
[    25.674] (II) Unloading modesetting
[    25.674] (II) Failed to load module "modesetting" (already loaded, 0)
[    25.674] (II) LoadModule: "fbdev"
[    25.674] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.674] (II) Module fbdev: vendor="X.Org Foundation"
[    25.674]     compiled for 1.15.1, module version = 0.4.4
[    25.674]     Module class: X.Org Video Driver
[    25.674]     ABI class: X.Org Video Driver, version 15.0
[    25.674] (II) UnloadModule: "fbdev"
[    25.674] (II) Unloading fbdev
[    25.674] (II) Failed to load module "fbdev" (already loaded, 0)
[    25.674] (II) LoadModule: "vesa"
[    25.674] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.674] (II) Module vesa: vendor="X.Org Foundation"
[    25.674]     compiled for 1.15.1, module version = 2.3.3
[    25.674]     Module class: X.Org Video Driver
[    25.674]     ABI class: X.Org Video Driver, version 15.0
[    25.674] (II) UnloadModule: "vesa"
[    25.674] (II) Unloading vesa
[    25.674] (II) Failed to load module "vesa" (already loaded, 0)
[    25.674] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    25.678] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.678] (II) FBDEV: driver for framebuffer: fbdev
[    25.678] (II) VESA: driver for VESA chipsets: vesa
[    25.678] (++) using VT number 7

[    25.712] (II) [KMS] Kernel modesetting enabled.
[    25.712] (WW) Falling back to old probe method for modesetting
[    25.712] (WW) Falling back to old probe method for fbdev
[    25.712] (II) Loading sub module "fbdevhw"
[    25.712] (II) LoadModule: "fbdevhw"
[    25.712] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.723] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.723]     compiled for 1.15.1, module version = 0.0.2
[    25.723]     ABI class: X.Org Video Driver, version 15.0
[    25.723] (WW) Falling back to old probe method for vesa
[    25.723] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.723] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    25.723] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    25.723] (==) RADEON(0): Default visual is TrueColor
[    25.723] (==) RADEON(0): RGB weight 888
[    25.723] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    25.723] (--) RADEON(0): Chipset: "SUMO" (ChipID = 0x9647)
[    25.723] (II) Loading sub module "dri2"
[    25.724] (II) LoadModule: "dri2"
[    25.724] (II) Module "dri2" already built-in
[    25.724] (II) Loading sub module "exa"
[    25.724] (II) LoadModule: "exa"
[    25.724] (II) Loading /usr/lib/xorg/modules/libexa.so
[    25.725] (II) Module exa: vendor="X.Org Foundation"
[    25.725]     compiled for 1.15.1, module version = 2.6.0
[    25.725]     ABI class: X.Org Video Driver, version 15.0
[    25.725] (II) RADEON(0): KMS Color Tiling: enabled
[    25.725] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    25.725] (II) RADEON(0): KMS Pageflipping: enabled
[    25.725] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    25.761] (II) RADEON(0): Output VGA-0 has no monitor section
[    25.801] (II) RADEON(0): Output LVDS has no monitor section
[    25.803] (II) RADEON(0): Output HDMI-0 has no monitor section
[    25.840] (II) RADEON(0): EDID for output VGA-0
[    25.879] (II) RADEON(0): EDID for output LVDS
[    25.879] (II) RADEON(0): Manufacturer: SEC  Model: 3454  Serial#: 0
[    25.879] (II) RADEON(0): Year: 2011  Week: 0
[    25.879] (II) RADEON(0): EDID Version: 1.3
[    25.879] (II) RADEON(0): Digital Display Input
[    25.879] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    25.879] (II) RADEON(0): Gamma: 2.20
[    25.879] (II) RADEON(0): No DPMS capabilities specified
[    25.879] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.879] (II) RADEON(0): First detailed timing is preferred mode
[    25.879] (II) RADEON(0): redX: 0.615 redY: 0.362   greenX: 0.348 greenY: 0.624
[    25.879] (II) RADEON(0): blueX: 0.146 blueY: 0.075   whiteX: 0.313 whiteY: 0.329
[    25.879] (II) RADEON(0): Manufacturer's mask: 0
[    25.879] (II) RADEON(0): Supported detailed timing:
[    25.879] (II) RADEON(0): clock: 107.8 MHz   Image Size:  382 x 215 mm
[    25.879] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1932 h_border: 0
[    25.879] (II) RADEON(0): v_active: 900  v_sync: 902  v_sync_end 907 v_blanking: 930 v_border: 0
[    25.879] (II) RADEON(0): Unknown vendor-specific block f
[    25.879] (II) RADEON(0):  SAMSUNG
[    25.879] (II) RADEON(0):  173KT02-H01
[    25.879] (II) RADEON(0): EDID (in hex):
[    25.879] (II) RADEON(0):     00ffffffffffff004ca3543400000000
[    25.879] (II) RADEON(0):     00150103802615780ab3959d5c599f25
[    25.879] (II) RADEON(0):     13505400000001010101010101010101
[    25.879] (II) RADEON(0):     0101010101011c2a404c61841e303020
[    25.879] (II) RADEON(0):     25007ed7100000190000000f00000000
[    25.879] (II) RADEON(0):     00000000002efa067800000000fe0053
[    25.879] (II) RADEON(0):     414d53554e470a2020202020000000fe
[    25.879] (II) RADEON(0):     003137334b5430322d4830310a200007
[    25.879] (II) RADEON(0): Printing probed modes for output LVDS
[    25.879] (II) RADEON(0): Modeline "1600x900"x60.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    25.879] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.879] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    25.879] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    25.879] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    25.879] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.879] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    25.879] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    25.879] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    25.879] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    25.879] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    25.882] (II) RADEON(0): EDID for output HDMI-0
[    25.882] (II) RADEON(0): Output VGA-0 disconnected
[    25.882] (II) RADEON(0): Output LVDS connected
[    25.882] (II) RADEON(0): Output HDMI-0 disconnected
[    25.882] (II) RADEON(0): Using exact sizes for initial modes
[    25.882] (II) RADEON(0): Output LVDS using initial mode 1600x900
[    25.882] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.882] (II) RADEON(0): mem size init: gart size :3fdee000 vram size: s:20000000 visible:1fa3b000
[    25.882] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    25.882] (==) RADEON(0): DPI set to (96, 96)
[    25.882] (II) Loading sub module "fb"
[    25.882] (II) LoadModule: "fb"
[    25.882] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.884] (II) Module fb: vendor="X.Org Foundation"
[    25.884]     compiled for 1.15.1, module version = 1.0.0
[    25.884]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.884] (II) Loading sub module "ramdac"
[    25.884] (II) LoadModule: "ramdac"
[    25.884] (II) Module "ramdac" already built-in
[    25.884] (II) UnloadModule: "modesetting"
[    25.884] (II) Unloading modesetting
[    25.884] (II) UnloadModule: "fbdev"
[    25.884] (II) Unloading fbdev
[    25.884] (II) UnloadSubModule: "fbdevhw"
[    25.884] (II) Unloading fbdevhw
[    25.884] (II) UnloadModule: "vesa"
[    25.884] (II) Unloading vesa
[    25.884] (--) Depth 24 pixmap format is 32 bpp
[    25.885] (II) RADEON(0): [DRI2] Setup complete
[    25.885] (II) RADEON(0): [DRI2]   DRI driver: r600
[    25.885] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    25.885] (II) RADEON(0): Front buffer size: 6000K
[    25.885] (II) RADEON(0): VRAM usage limit set to 461113K
[    25.885] (==) RADEON(0): Backing store enabled
[    25.885] (II) RADEON(0): Direct rendering enabled
[    25.885] (II) EXA(0): Driver allocated offscreen pixmaps
[    25.885] (II) EXA(0): Driver registered support for the following operations:
[    25.885] (II)         Solid
[    25.885] (II)         Copy
[    25.885] (II)         Composite (RENDER acceleration)
[    25.885] (II)         UploadToScreen
[    25.885] (II)         DownloadFromScreen
[    25.885] (II) RADEON(0): Acceleration enabled
[    25.886] (==) RADEON(0): DPMS enabled
[    25.886] (==) RADEON(0): Silken mouse enabled
[    25.886] (II) RADEON(0): Set up textured video
[    25.886] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    25.886] (II) RADEON(0): [XvMC] Extension initialized.
[    25.886] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.887] (--) RandR disabled
[    26.880] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.880] (II) AIGLX: enabled GLX_ARB_create_context
[    26.880] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    26.880] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    26.880] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.880] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.880] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    26.880] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    26.880] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.881] (II) AIGLX: Loaded and initialized r600
[    26.881] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.948] (II) RADEON(0): Setting screen physical size to 423 x 238
[    27.049] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.063] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.063] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.063] (II) LoadModule: "evdev"
[    27.063] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.093] (II) Module evdev: vendor="X.Org Foundation"
[    27.093]     compiled for 1.15.1, module version = 2.8.2
[    27.093]     Module class: X.Org XInput Driver
[    27.093]     ABI class: X.Org XInput driver, version 20.0
[    27.093] (II) Using input driver 'evdev' for 'Power Button'
[    27.093] (**) Power Button: always reports core events
[    27.093] (**) evdev: Power Button: Device: "/dev/input/event2"
[    27.093] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.093] (--) evdev: Power Button: Found keys
[    27.093] (II) evdev: Power Button: Configuring as keyboard
[    27.093] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    27.093] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.093] (**) Option "xkb_rules" "evdev"
[    27.093] (**) Option "xkb_model" "pc105"
[    27.093] (**) Option "xkb_layout" "us"
[    27.094] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    27.094] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.094] (II) Using input driver 'evdev' for 'Video Bus'
[    27.094] (**) Video Bus: always reports core events
[    27.094] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    27.094] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.094] (--) evdev: Video Bus: Found keys
[    27.094] (II) evdev: Video Bus: Configuring as keyboard
[    27.094] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event5"
[    27.094] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.094] (**) Option "xkb_rules" "evdev"
[    27.094] (**) Option "xkb_model" "pc105"
[    27.094] (**) Option "xkb_layout" "us"
[    27.094] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.094] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.094] (II) Using input driver 'evdev' for 'Power Button'
[    27.094] (**) Power Button: always reports core events
[    27.094] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.094] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.094] (--) evdev: Power Button: Found keys
[    27.094] (II) evdev: Power Button: Configuring as keyboard
[    27.094] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.094] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    27.094] (**) Option "xkb_rules" "evdev"
[    27.094] (**) Option "xkb_model" "pc105"
[    27.094] (**) Option "xkb_layout" "us"
[    27.095] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    27.095] (II) No input driver specified, ignoring this device.
[    27.095] (II) This device may have been added with another device file.
[    27.095] (II) config/udev: Adding drm device (/dev/dri/card0)
[    27.095] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.095] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event8)
[    27.095] (II) No input driver specified, ignoring this device.
[    27.095] (II) This device may have been added with another device file.
[    27.096] (II) config/udev: Adding input device HP Webcam-101 (/dev/input/event11)
[    27.096] (**) HP Webcam-101: Applying InputClass "evdev keyboard catchall"
[    27.096] (II) Using input driver 'evdev' for 'HP Webcam-101'
[    27.096] (**) HP Webcam-101: always reports core events
[    27.096] (**) evdev: HP Webcam-101: Device: "/dev/input/event11"
[    27.096] (--) evdev: HP Webcam-101: Vendor 0x461 Product 0x4de7
[    27.096] (--) evdev: HP Webcam-101: Found keys
[    27.096] (II) evdev: HP Webcam-101: Configuring as keyboard
[    27.096] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input12/event11"
[    27.096] (II) XINPUT: Adding extended input device "HP Webcam-101" (type: KEYBOARD, id 9)
[    27.096] (**) Option "xkb_rules" "evdev"
[    27.096] (**) Option "xkb_model" "pc105"
[    27.096] (**) Option "xkb_layout" "us"
[    27.096] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event10)
[    27.096] (II) No input driver specified, ignoring this device.
[    27.096] (II) This device may have been added with another device file.
[    27.096] (II) config/udev: Adding input device HD-Audio Generic Front Headphone (/dev/input/event9)
[    27.096] (II) No input driver specified, ignoring this device.
[    27.096] (II) This device may have been added with another device file.
[    27.097] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.097] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.097] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.097] (**) AT Translated Set 2 keyboard: always reports core events
[    27.097] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.097] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.097] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.097] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.097] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    27.097] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    27.097] (**) Option "xkb_rules" "evdev"
[    27.097] (**) Option "xkb_model" "pc105"
[    27.097] (**) Option "xkb_layout" "us"
[    27.097] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    27.097] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.097] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.097] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    27.097] (II) LoadModule: "synaptics"
[    27.098] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.110] (II) Module synaptics: vendor="X.Org Foundation"
[    27.110]     compiled for 1.15.1, module version = 1.7.4
[    27.110]     Module class: X.Org XInput Driver
[    27.110]     ABI class: X.Org XInput driver, version 20.0
[    27.110] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.110] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.110] (**) Option "Device" "/dev/input/event7"
[    27.132] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728 (res 46)
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4828 (res 70)
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    27.132] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.132] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.148] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event7"
[    27.148] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    27.148] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.148] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    27.148] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    27.148] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.148] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.148] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.148] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.148] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.149] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.149] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.150] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event4)
[    27.150] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.150] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    27.150] (**) HP Wireless hotkeys: always reports core events
[    27.150] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event4"
[    27.150] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    27.150] (--) evdev: HP Wireless hotkeys: Found keys
[    27.150] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    27.150] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event4"
[    27.150] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 12)
[    27.150] (**) Option "xkb_rules" "evdev"
[    27.150] (**) Option "xkb_model" "pc105"
[    27.150] (**) Option "xkb_layout" "us"
[    27.151] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    27.151] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.151] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    27.151] (**) HP WMI hotkeys: always reports core events
[    27.151] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event6"
[    27.151] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    27.151] (--) evdev: HP WMI hotkeys: Found keys
[    27.151] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    27.151] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event6"
[    27.151] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    27.151] (**) Option "xkb_rules" "evdev"
[    27.151] (**) Option "xkb_model" "pc105"
[    27.151] (**) Option "xkb_layout" "us"
[    31.874] (II) RADEON(0): EDID vendor "SEC", prod id 13396
[    31.874] (II) RADEON(0): Printing DDC gathered Modelines:
[    31.874] (II) RADEON(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    43.128] (II) RADEON(0): EDID vendor "SEC", prod id 13396
[    43.128] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.128] (II) RADEON(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    45.502] (II) RADEON(0): EDID vendor "SEC", prod id 13396
[    45.502] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.502] (II) RADEON(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    55.365] (II) RADEON(0): EDID vendor "SEC", prod id 13396
[    55.365] (II) RADEON(0): Printing DDC gathered Modelines:
[    55.365] (II) RADEON(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)
[    56.028] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[    65.929] (II) RADEON(0): EDID vendor "SEC", prod id 13396
[    65.929] (II) RADEON(0): Printing DDC gathered Modelines:
[    65.929] (II) RADEON(0): Modeline "1600x900"x0.0  107.80  1600 1648 1680 1932  900 902 907 930 -hsync -vsync (55.8 kHz eP)


```

---

