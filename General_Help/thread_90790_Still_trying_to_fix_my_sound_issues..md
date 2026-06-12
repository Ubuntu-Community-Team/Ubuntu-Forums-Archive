---
title: "Still trying to fix my sound issues."
date: 2005-11-15
forum: General Help
---

### Post by Statik on 2005-11-15
Hi all.

I have this motherboard: [http://www.msicomputer.com/product/p_spec.asp?model=K7N2_Delta2-FSR&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=K7N2_Delta2-FSR&class=mb)

I'm trying to get the sound to work without the oss errors in Doom3. Everything else seems to work fine.

I decided to try the nvidia drivers. It failed. Here is the output:
```

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Tue Nov 15 20:55:06 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-6)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.12-9-k7 (buildd@rothera) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:47:52
   BST 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.12-9-k7/build'
-> Kernel output path: '/lib/modules/2.6.12-9-k7/build'
-> Performing cc_version_check with CC="cc".
-> gcc-version-check failed:
   
   You appear to be compiling the NVIDIA kernel module with a different compile
   r than the one that was used to compile the running kernel.  This may be fin
   e, but there are cases where this can lead to instability.  The compiler use
   d to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.12-9-k7/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.12-9-k7/b
   uild SYSOUT=/lib/modules/2.6.12-9-k7/build'...
   make -C /lib/modules/2.6.12-9-k7/build		\
   KBUILD_SRC=/usr/src/linux-headers-2.6.12-9-k7	     KBUILD_VERBOSE=1	\
   KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1
   /nvsound/main"	\
           -f /usr/src/linux-headers-2.6.12-9-k7/Makefile modules
   mkdir -p /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.tmp_v
   ersions
   make -f /usr/src/linux-headers-2.6.12-9-k7/scripts/Makefile.build obj=/tmp/s
   elfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.n
   valinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D
   __KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.12-9-k7/include
    -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main -Wall -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding
   -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fn
   o-unit-at-a-time -march=athlon -I/usr/src/linux-headers-2.6.12-9-k7/include/
   asm-i3
   86/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statemen
   t -Wno-pointer-sign  -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsou
   nd/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -
   Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -W
   no-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE
   -DKBUILD_BASENAME=nvalinux -DKBUILD_MODNAME=nvsound -c -o /tmp/selfgz16938/N
   FORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.tmp_nvalinux.o /tmp/selfgz16938/
   NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvalinux.c:19:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvalinux.c:25:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.n
   vmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D_
   _KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.12-9-k7/include 
   -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main -Wall -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding 
   -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fn
   o-unit-at-a-time -march=athlon -I/usr/src/linux-headers-2.6.12-9-k7/include/
   asm-i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-st
   atement -Wno-pointer-sign  -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1
   /nvsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-q
   ual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -D
   MODULE -DKBUILD_BASENAME=nvmixer -DKBUILD_MODNAME=nvsound -c -o /tmp/selfgz1
   6938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.tmp_nvmixer.o /tmp/selfgz1
   6938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvhw.h:29,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvmixer.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvhw.h:35,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvmixer.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.n
   vmain.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__
   KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.12-9-k7/include  
   -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main -Wall -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding 
   -O2 -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -fn
   o-unit-at-a-time -march=athlon -I/usr/src/linux-headers-2.6.12-9-k7/include/
   asm-i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-st
   atement -Wno-pointer-sign  -I/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1
   /nvsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wn
   o-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PR
   ESENT -DMODULE -DKBUILD_BASENAME=nvmain -DKBUILD_MODNAME=nvsound -c -o /tmp/
   selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.tmp_nvmain.o /tmp/s
   elfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvmain.c:27:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvhw.h:35,
                    from /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsoun
   d/main/nvmain.c:29:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     ld -m elf_i386 -d -r -o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nv
   sound/main/nvsound.o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound
   /main/mcpmain.o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main
   /nvalinux.o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvm
   ixer.o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvmain.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.12-9-k7/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.12-9-k7/Module.sym
   vers /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvsound.o
   Warning: could not find /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvso
   und/main/.mcpmain.o.cmd for /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/
   nvsound/main/mcpmain.o
     cc -Wp,-MD,/tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/.n
   vsound.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include
   -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.12-9-k7/inclu
   de -I/usr/src/linux-headers-2.6.12-9-k7/ -I -Wall -Wstrict-prototypes -Wno-t
   rigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 -fomit-frame-po
   inter -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -m
   arch=athlon -I/usr/src/linux-headers-2.6.12-9-k7/include/asm-i386/mach-defau
   lt -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointe
   r-sign  -DKBUILD_BASENAME=nvsound -DKBUILD_MODNAME=nvsound -DMODULE -c -o /t
   mp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvsound.mod.o /tm
   p/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/nvsound.mod.c
     ld -m elf_i386 -r -o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsou
   nd/main/nvsound.ko /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/m
   ain/nvsound.o /tmp/selfgz16938/NFORCE-Linux-x86-1.0-0306-pkg1/nvsound/main/n
   vsound.mod.o
-> done.
-> Kernel module compilation complete.
-> Testing kernel module:
-> Copying test module ./nvsound/main/nvsound.ko to
   /lib/modules/2.6.12-9-k7/kernel/sound/oss/nvsound.ko
ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvsound
   (/lib/modules/2.6.12-9-k7/kernel/sound/oss/nvsound.ko): Invalid module
   format
-> Testing completed.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```

Any idea on why it fails? I'm a nub. However, I did follow the instructions and get my kernal version (2.6.12-9-k7) and install the header and source files as instructed in one of the threads.

Statik

---

### Post by Remmelas on 2005-11-15
try putting
CC=/usr/bin/gcc-3.4
in front of your command you use to install, that will at least get you compiling with the right compiler, may solf the problem.
so, like this
CC=/usr/bin/gcc-3.4 nvidia_install_command_here

---

### Post by Statik on 2005-11-16
Had to install gcc-3.4 had gcc-3.3 and gcc-4.0 installed. 3.4 is the only one that would work. Now, I'm reading through the releasenotes and I'm lost again. I have the driver built. Now what?

Statik

---

### Post by Statik on 2005-11-16
BTW, doom3 is setting alsa this way:
```

------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.9
opened Alsa PCM device plughw:0 for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes

```

And then I get the errors this way:
```

Async thread started
snd_pcm_writei short write: 4095 out of 4096
snd_pcm_writei short write: 4095 out of 4096
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
snd_pcm_writei short write: 1022 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped

```

Wish I could figure this stuff out.

*sigh*

Statik

---

### Post by Statik on 2005-11-18
ok, I finally have my nvsound working . . . it's not perfect, but it's working.

```
statik@ubuntu:~$ lsmod
Module                  Size  Used by
nls_cp437               5760  1
isofs                  36664  1
udf                    92356  0
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0
cpufreq_stats           5316  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
fglrx                 255716  7
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252480  10
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
nvsound              1543224  1
soundcore               9696  2 nvsound
i2c_nforce2             6784  0
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              8412  1
agpgart                34888  2 fglrx,nvidia_agp
dm_mod                 58044  1
tsdev                   7872  0
evdev                   9728  0
sr_mod                 17252  0
sbp2                   23176  0
ieee1394              101752  1 sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  1
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
usbhid                 35552  0
forcedeth              21568  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118204  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 19216  3
ide_cd                 41732  1
cdrom                  39904  2 sr_mod,ide_cd
ide_disk               18560  2
ide_generic             1472  0
sata_nv                 9412  4
libata                 54020  1 sata_nv
scsi_mod              135944  4 sr_mod,sbp2,sd_mod,libata
amd74xx                14044  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   27248  997
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon
```

NVMIXER reports:
Nvidia Product Name: nForce Audio
Hardware Model: nForce2 MCP2S
Hardware Revision: a1
Ausio Driver Version: 1.0-6
Linux Kernel Version: 2.6.12
Codec Manufacturer: Realtek
Codec Model: ALC655
Codec Capabilities: 1 Codec, 6 Channels

Still trying to get Doom3-demo to work.
if I don't killall esd, then doom3 cannot find /dev/dsp. If I kill esd, then I get the error:
```
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.WARNING: ioctl SNDCTL_DSP_SPEED failed to get the requested frequency 44100, got 48000
close sound device
WARNING: sound subsystem disabled

```

Got sound in the system by installing the libesd0 package so that esd used oss.

Working on getting sound back in flash files now

Statik

---

### Post by Statik on 2005-11-22
I cannot get sound working for Flash. Neither FIrefox nor Epiphany. I've searched and searched, and nothing so far. Tried using auto, aoss and none in the firefox settings, nothing works. Tried removing my asound.conf, still nothing.

Any ideas?

Statik

---

