---
title: "Installation of NVIDIA-Drivers for GE Force 210 - Kubuntu 13.10"
date: 2014-02-15
forum: Hardware
---

### Post by Detlef_Bracker on 2014-02-15
I prefare german language when its possible!

Dear, I hope one can help me:

I have read and follow 100 diferent installation instructions for NVIDIA-Drivers and all brings diferent errors!
I have remove all something nvidia* - I have install and test diferent drivers - Everytime a other horror!
Before I had an other Graphic Card GE Force 9500 GT - with this card the computer many times frozen - but this graphic card I must change about one day this not working fine.

OK - First the equipment:

OS: Kubuntu 13.10 - with Kernel 3.11.0.15
a) ASUS-Mainboard PV5VD2MX
b) Internal Graphic-Card on Bord (I used only in the middle of time - other graphic card was broken in VESA-Mode)
c) Graphic-Card GE Force 210 Giganet
d) Monitor 0: XPhonenix (normal in Mode 1024x768)
e) Monitor 1: Samsung S22C150  (max 1920x1080) - will using in: 1280x.... - I cant see in moment via xrandr - before yes

Monitor 0 left XINERAMA Monitor 1 right

Monitor 0 shows me in moment nothing
Monitor 1 in 1024x768 - Modes (fluckering)

yesterday in 1920x1080 - without a possiblity to change the resolution

Time to use diferent drivers Installations more as 48 working hours!

lshw -C display:

PCI (sysfs)  
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:dd000000-ddffffff memory:b0000000-bfffffff memory:ce000000-cfffffff ioport:cc00(size=128) memory:def00000-def7ffff
root@dbmaster:~# 

root@dbmaster:~# ps -ef | grep X
root      1840  1821  3 11:36 tty7     00:02:20 /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch

root@dbmaster:~# xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
root@dbmaster:~# 

root@dbmaster:~# jockey-text -l
ERROR:root:Could not find any typelib for AppIndicator3
kmod:nvidia_319_updates - nvidia_319_updates (Propriet&#258;¤r, Aktiviert, Nicht benutzt)
kmod:nvidia_331 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Frei, Deaktiviert, Nicht benutzt)
kmod:nvidia_304_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Propriet&#258;¤r, Deaktiviert, Nicht benutzt)
kmod:nvidia_304 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Frei, Deaktiviert, Nicht benutzt)
root@dbmaster:~# 

Xorg-configure create this file with error, they find more or less displays as installed or so:

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        Screen      2  "Screen2" RightOf "Screen1"
        Screen      3  "Screen3" RightOf "Screen2"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Monitor"
        Identifier   "Monitor2"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Monitor"
        Identifier   "Monitor3"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "WrappedFB"                 # [<bool>]
        #Option     "GLXVBlank"                 # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        #Option     "PageFlip"                  # [<bool>]
        #Option     "SwapLimit"                 # <i>
        #Option     "AsyncUTSDFS"               # [<bool>]
        Identifier  "Card0"
        Driver      "nouveau"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "kmsdev"                    # <str>
        #Option     "ShadowFB"                  # [<bool>]
        Identifier  "Card1"
        Driver      "modesetting"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # <str>
        #Option     "fbdev"                     # <str>
        #Option     "debug"                     # [<bool>]
        Identifier  "Card2"
        Driver      "fbdev"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "DefaultRefresh"            # [<bool>]
        #Option     "ModeSetClearScreen"        # [<bool>]
        Identifier  "Card3"
        Driver      "vesa"
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen2"
        Device     "Card2"
        Monitor    "Monitor2"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen3"
        Device     "Card3"
        Monitor    "Monitor3"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

With jockey when a driver is selected and in green, I get every time, that this driver is activated, but not in using!

I have test too:

apt-get purge xserver-xorg
agt-get install sserver-xorg xserver-xorg-video-all

and / or

apt-get purge nvidia*
apt-get update
apt-get install nvida-current
Xorg -configure
nvidia-settings
nvidia-xconfig
update-grub

jockey-text -e Xorg:nvidia-current OR kmod:nvidia-304

I have too install linux-firmware-nonfree


Dear

Detlef

---

### Post by Detlef_Bracker on 2014-02-16
So, I have start again, to install nvidia-driver:

I will install the driver from NVIDIA direct:

The Preparation was:

apt-get install build-essential xserver-xorg-dev linux-headers-generic
stop lightdm

Then:

sudo sh NVIDIA-Linux-x86-319.17.run

DKMS = yes

Errors:

DKMS make.log for nvidia-319.17 for kernel 3.11.0-15-generic (i686)
Sun Feb 16 08:13:56 CET 2014
NVIDIA: calling KBUILD...
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia/319.17/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/319.17/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/319.17/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv.o /var/lib/dkms/nvidia/319.17/build/nv.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-acpi.o /var/lib/dkms/nvidia/319.17/build/nv-acpi.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c: At top level:
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c:70:9: warning: initialization from incompatible pointer type [enabled by default]
         .remove = nv_acpi_remove,
         ^
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c:70:9: warning: (near initialization for 'nv_acpi_driver_template.ops.remove') [enabled by default]
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-acpi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-chrdev.o /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-chrdev.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-cray.o /var/lib/dkms/nvidia/319.17/build/nv-cray.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-cray.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-drm.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_drm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-drm.o /var/lib/dkms/nvidia/319.17/build/nv-drm.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
In file included from include/drm/drm_crtc.h:32:0,
                 from include/drm/drmP.h:688,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:19:
include/linux/fb.h: In function '__fb_pad_aligned_buffer':
include/linux/fb.h:650:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (j = 0; j < s_pitch; j++)
                 ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-drm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-drm.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-gvi.o /var/lib/dkms/nvidia/319.17/build/nv-gvi.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-gvi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-i2c.o /var/lib/dkms/nvidia/319.17/build/nv-i2c.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-i2c.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-i2c.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-i2c.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
/var/lib/dkms/nvidia/319.17/build/nv-i2c.c: In function 'nv_i2c_del_adapter':
/var/lib/dkms/nvidia/319.17/build/nv-i2c.c:327:14: error: void value not ignored as it ought to be
     osstatus = i2c_del_adapter(pI2cAdapter);
              ^
make[3]: *** [/var/lib/dkms/nvidia/319.17/build/nv-i2c.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/319.17/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2

OK, then the debugging of /var/lib/dkms/nvidia/319.17/build/make.log:

DKMS make.log for nvidia-319.17 for kernel 3.11.0-15-generic (i686)
Sun Feb 16 08:13:56 CET 2014
NVIDIA: calling KBUILD...
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo >&2;                            \
    echo >&2 "  ERROR: Kernel configuration is invalid.";        \
    echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo >&2 ;                            \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia/319.17/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/319.17/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/319.17/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv.o /var/lib/dkms/nvidia/319.17/build/nv.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv.c:13:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-acpi.o /var/lib/dkms/nvidia/319.17/build/nv-acpi.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-acpi.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c: At top level:
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c:70:9: warning: initialization from incompatible pointer type [enabled by default]
         .remove = nv_acpi_remove,
         ^
/var/lib/dkms/nvidia/319.17/build/nv-acpi.c:70:9: warning: (near initialization for 'nv_acpi_driver_template.ops.remove') [enabled by default]
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-acpi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-chrdev.o /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-chrdev.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-chrdev.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-cray.o /var/lib/dkms/nvidia/319.17/build/nv-cray.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-cray.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-cray.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-drm.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_drm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-drm.o /var/lib/dkms/nvidia/319.17/build/nv-drm.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
In file included from include/drm/drm_crtc.h:32:0,
                 from include/drm/drmP.h:688,
                 from /var/lib/dkms/nvidia/319.17/build/nv-drm.c:19:
include/linux/fb.h: In function '__fb_pad_aligned_buffer':
include/linux/fb.h:650:17: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   for (j = 0; j < s_pitch; j++)
                 ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-drm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-drm.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-gvi.o /var/lib/dkms/nvidia/319.17/build/nv-gvi.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/cpumask.h:4:0,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/uapi/linux/timex.h:56,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:17,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
include/linux/cpumask.h: In function 'cpumask_parse':
include/linux/cpumask.h:603:26: warning: signed and unsigned type in conditional expression [-Wsign-compare]
  int len = nl ? nl - buf : strlen(buf);
                          ^
In file included from include/uapi/linux/stddef.h:1:0,
                 from include/linux/stddef.h:4,
                 from /usr/src/linux-headers-3.11.0-15-generic/include/uapi/linux/posix_types.h:4,
                 from include/uapi/linux/types.h:13,
                 from include/linux/types.h:5,
                 from include/uapi/linux/capability.h:16,
                 from include/linux/capability.h:15,
                 from include/linux/sched.h:13,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-gvi.c:15:
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h: In function 'copy_from_user':
/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/uaccess_32.h:208:28: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  if (likely(sz == -1 || sz >= n))
                            ^
include/linux/compiler.h:152:40: note: in definition of macro 'likely'
 # define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia/319.17/build/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.11.0-15-generic/scripts/recordmcount  "/var/lib/dkms/nvidia/319.17/build/nv-gvi.o"; fi; fi;
  cc -Wp,-MD,/var/lib/dkms/nvidia/319.17/build/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include  -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include -Iarch/x86/include/generated  -Iinclude -I/usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I/usr/src/linux-headers-3.11.0-15-generic/include/uapi -Iinclude/generated/uapi -include /usr/src/linux-headers-3.11.0-15-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -pipe -Wno-sign-compare -fno-
asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia/319.17/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"319.17\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG -D__linux__  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia/319.17/build/.tmp_nv-i2c.o /var/lib/dkms/nvidia/319.17/build/nv-i2c.c
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/include/asm/bitops.h:514:0,
                 from include/linux/bitops.h:22,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:15,
                 from include/linux/utsname.h:5,
                 from /var/lib/dkms/nvidia/319.17/build/nv-linux.h:44,
                 from /var/lib/dkms/nvidia/319.17/build/nv-i2c.c:15:
include/linux/bitops.h: In function 'hweight_long':
include/asm-generic/bitops/const_hweight.h:26:70: warning: signed and unsigned type in conditional expression [-Wsign-compare]
 #define hweight32(w) (__builtin_constant_p(w) ? __const_hweight32(w) : __arch_hweight32(w))
                                                                      ^
include/linux/bitops.h:66:26: note: in expansion of macro 'hweight32'
  return sizeof(w) == 4 ? hweight32(w) : hweight64(w);
                          ^
In file included from /usr/src/linux-headers-3.11.0-15-generic/arch/x86/inclu

---

### Post by Detlef_Bracker on 2014-02-16
WORKARROUND for all users, they have problems to install the NVIDIA-DRIVER - The installation is very buggy!

The Best ist the Nvidia-Driver 319.60 - but when you make a download direct from nvidia you get every time 319.17 and most users have a problem to install this via the run-script in Kubunto 13.10. When its so,

make a download via apt-get or aptitude of nvidia-319-updates.
Then been careful, that you have installed too the [COLOR=#111111][FONT=Verdana]nvidia-310 and [/FONT][/COLOR][COLOR=#111111][FONT=Verdana]nvidia-310-dev
By me the Package nvida-310-dev was not installed and this possible create big problems.

Ok, when this are installed, then change into a konsole - window. 

Their you enter to activate the driver

sudo -i
jockey-text -e kmod:nvidia-319-updates

Then you must wait 1 to 3 minutes and possible, you see, that the driver is activated!

When its going correct, make a 

nvidia-xconfig

and then make a reboot

This works fine, only the resolution can been wrong, but we will correct this in the next step!


So, now we will make a correction of the resolution, why Nvidia-settings possible not working!

We do this on the console:

sudo -i

xrandr 

I hope, you get something and see your displays, expl. VGA or VGA-1. This is different of your hardware (graphic card) and possible you must adapt this:

OK, you see for every Display (when you use more as one Monitor/Flat-Screen) and possible your monitors has the wrong resulution.

When your monitor has a higher resolution, as in the list is possible, you must first find the modes (resolutions), that this monitor can use. When you dont know the highest resolution, search in internet your hardware model and the max resolution. Then you enter the max resolution with:

gtf 1920 1080 60 

where 1920x1080 60 Hz

Then you get a line 

[/FONT][/COLOR]Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

Ok, this we must insert in xrandr, explo so:

xrandr --newmode "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

So, then this is not linked to your display (monitor) - we will do this now:

xrandr --addmode DVI-I-1 1920x1080

Ok, now we have set the highest resolution to the display DVI-I-1 but we will not used the highes resolution,
we will use expl. one between - so now you can add an other too:

xrandr --addmode DVI-I-1 1280x1024

Ok, now its possible to select the 2 new inserted resolutions and the others, they was listed before. 

Now we will change the resolution for the display:

xrandr --output DVI-I-1 --mode 1280x1024

and example the resolution for the other display

xrandr --output VGA-1 --mode 1024x768

Save your settings in a text file please, why you need your settings for a profile for this user again - otherwise when the machine is rebooted, your have lost all!

In many documentation of ubuntu / xrandr they have written you can put in in a file /home/Username/.xprofile as an example:

xrandr --newmode "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
xrandr --addmode DVI-I-1 1920x1080
xrandr --addmode DVI-I-1 1280x1024
xrandr --output DVI-I-1 --mode 1280x1024

OK, when you have saved this file in your HOME-Directory, expl. in /home/YourName/.xprofile
you must then change the file to executable - in a console:

sudu -i
chmod 744 /home/YourName/.xprofile

Now you can easy test this, you must not reboot, you can test via:

Start-Button -> Verlassen -> Abmelden
Start-Button -> Shutdown/Quit -> Logoff

When you logoff, you will see the standard resolutions and when you have loged in,
you see your resolutions, so as before and saved!

I hope I have help many users

[1awww.com]("http://1awww.com") - Internet-Service-Provider

Detlef Bracker

---

### Post by Stoatwblr on 2014-03-16
Do you have 2 or 4 screens on this setup?

---

