---
title: "audio drivers"
date: 2008-09-24
forum: General Help
---

### Post by gabitzu4224 on 2008-09-24
i recently installed ubuntu and im very pleased with it. It is very user-friendly, almost everything is easy to install and configure, except the sound drivers, which dont seem to be present. I tried installing alsa but that didnt help. Does ubuntu normally detect and install the sound drivers?  
This is the output for the sound card from lspci, maybe it will help:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

---

### Post by northern lights on 2008-09-24
> **gabitzu4224 said:**
> Does ubuntu normally detect and install the sound drivers?
Depends on the device.

> **gabitzu4224 said:**
> I tried installing alsa but that didnt help. 
alsa should be set up by default...

> **gabitzu4224 said:**
> This is the output for the sound card from lspci, maybe it will help:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
Can you also post the output of ```
sudo lshw -C multimedia
```
Thank you.

Further, [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") might be a worthy read.

---

### Post by gabitzu4224 on 2008-09-25
this is the output for lshw -C multimedia:

```
 *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```


I also followed the instructions from the alsa installation page. All went well until I gave the sudo make command while in the alsa-driver folder. The rest compiled and installed (apparently) with succes. This is the error from the sudo make :

```

make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa/alsa-driver-1.0.9rc4a/include  -I/usr/src/linux-headers-2.6.24-19-generic/include -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /usr/src/linux-headers-2.6.24-19-generic/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /usr/src/linux-headers-2.6.24-19-generic/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/current_64.h:7,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/current.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:17,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/pda.h:39: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/pda.h:39: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:22,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:79: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:200: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:35,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/elf.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/elf.h:6,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:14,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:29:1: warning: this is the location of the previous definition
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/elf.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/elf.h:6,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:14,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h: In function ‘user_mode’:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: for each function it appears in.)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: ‘USER_RPL’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h: In function ‘user_mode_vm’:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:54: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:54: error: ‘USER_RPL’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/slab.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/local_64.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:19,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:74: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:124: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:342: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/hardirq_64.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/hardirq.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/irq.h:178: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:54,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:75,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/rcupdate.h:72: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/rcupdate.h:75: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:78,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/timer.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:87,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/ktime.h: In function ‘ktime_set’:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/ktime.h:84: warning: comparison is always false due to limited range of data type
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1
```

---

### Post by northern lights on 2008-09-25
> **gabitzu4224 said:**
> 
I also followed the instructions from the alsa installation page. All went well until I gave the sudo make command while in the alsa-driver folder. The rest compiled and installed (apparently) with succes.Again, alsa should already be installed. Run ```
aptitude search alsa
```'alsa' should have a 'v' flag and 'alsa-base' as well as 'alsa-utils' should be flagged 'i'.


> **gabitzu4224 said:**
> ```
 *-multimedia _UNCLAIMED_  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
```
Your audio device has not been assigned a driver. This is your core problem.

Please further check the nature of your card by means of```
aplay -l
```Post results. Thanks.

---

### Post by gabitzu4224 on 2008-09-26
ok this is the output for the aptitude search alsa, looks like i do have alsa installed:

```
v   alsa                            -                                           
i   alsa-base                       - ALSA driver configuration files           
p   alsa-firmware-loaders           - ALSA software loaders for specific hardwar
p   alsa-oss                        - ALSA wrapper for OSS applications         
p   alsa-source                     - ALSA driver sources                       
p   alsa-tools                      - Console based ALSA utilities for specific 
p   alsa-tools-gui                  - GUI based ALSA utilities for specific hard
i   alsa-utils                      - ALSA utilities                            
p   alsamixergui                    - graphical soundcard mixer for ALSA soundca
v   alsaplayer                      -                                           
p   alsaplayer-alsa                 - PCM player designed for ALSA (ALSA output 
p   alsaplayer-common               - PCM player designed for ALSA (common files
p   alsaplayer-daemon               - PCM player designed for ALSA (non-interact
p   alsaplayer-esd                  - PCM player designed for ALSA (EsounD outpu
p   alsaplayer-gtk                  - PCM player designed for ALSA (GTK version)
v   alsaplayer-interface            -                                           
p   alsaplayer-jack                 - PCM player designed for ALSA (JACK output 
p   alsaplayer-nas                  - PCM player designed for ALSA (NAS output m
p   alsaplayer-oss                  - PCM player designed for ALSA (OSS output m
v   alsaplayer-output               -                                           
p   alsaplayer-text                 - PCM player designed for ALSA (text version
p   alsaplayer-xosd                 - PCM player designed for ALSA (osd version)
p   balsa                           - An e-mail client for GNOME                
p   balsa-dbg                       - An e-mail client for GNOME                
p   bluetooth-alsa                  - Bluetooth audio for Linux                 
p   bse-alsa                        - ALSA plugin for BEAST                     
p   gnome-alsamixer                 - ALSA sound mixer for GNOME                
i   gstreamer0.10-alsa              - GStreamer plugin for ALSA                 
p   libalsa-ocaml                   - OCaml bindings for the ALSA library       
p   libalsa-ocaml-dev               - OCaml bindings for the ALSA library       
p   libalsaplayer-dev               - PCM player designed for ALSA (interface li
p   libalsaplayer0                  - PCM player designed for ALSA (interface li
p   libclalsadrv-dev                - Development file for libclalsadrv         
p   libclalsadrv1                   - ALSA driver C++ access library            
i   libesd-alsa0                    - Enlightened Sound Daemon (ALSA) - Shared l
i   libpt-1.10.10-plugins-alsa      - Portable Windows Library Audio Plugin for 
p   libpt-1.11.2-plugins-alsa       - Portable Windows Library Audio Plugin for 
i   libsdl1.2debian-alsa            - Simple DirectMedia Layer (with X11 and ALS
p   libsox-fmt-alsa                 - SoX alsa format I/O library               
p   mpg123-alsa                     - MPEG layer 1/2/3 audio player with ALSA su
p   psemu-sound-alsa                - ALSA sound plugin for PSX emulators       
p   python-alsaaudio                - Alsa bindings for Python                  
v   snd-gtk-alsa                    -                                           
p   vlc-plugin-alsa                 - dummy transitional package                
p   xfce4-mixer-alsa                - Xfce4 Mixer ALSA backend                  
p   xmms2-plugin-alsa               - XMMS2 - ALSA output                       
p   yate-alsa                       - ALSA module for yate                      

```


and aplay -l shows :

```
**** List of PLAYBACK Hardware Devices ****
```


ok so how do i assign the sound driver to the hardware?

---

