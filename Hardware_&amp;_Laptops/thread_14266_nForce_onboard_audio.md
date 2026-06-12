---
title: "nForce onboard audio"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by Arktis on 2005-02-05
Hiya.
  
  I wanna start off by saying that I do have sound.  Just not for everything.
  
 I have a K7N2 Delta Motherboard with the nForce chipset. I can listen to music and hear sound events, however there is no audio at all for flash player, and some games that use hardware like tux racer and bzflag don't have sound either. So I went and got the nForce unified driver [here]("http://www.nvidia.com/object/linux_nforce_1.0-0292.html") and proceeded to install the sucker.
  
 During the installation it told me that "No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface."
  
  Joy.
  
 So I said "OK" and then I get "ERROR: The NVIDIA kernel module was not created." So I quit that and made sure I had linux-source installed. Then I checked the output of '/var/log/nvidia-nforce-installer.log like the installer told me to. Here is that :
  
  ```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
  creation time: Sat Feb  5 20:05:21 2005
  
  option status:
    license pre-accepted	  : false
    expert				    : false
    uninstall				 : false
    driver info			   : false
    no precompiled interface  : false
    no ncurses color		  : false
    no questions			  : false
    silent				    : false
    Installer install prefix  : /usr
    kernel source path		: (not specified)
    net kernel install path   : (not specified)
    audio kernel install path : (not specified)
    proc mount point		  : /proc
 ui					 : (not specified)
    tmpdir				    : /tmp
  
  Using: nvidia-installer ncurses user interface
  -> Found package NVIDIA network driver for Linux-x86
  -> Found package NVIDIA audio driver for Linux-x86
  -> Please select packages for installation:
     Selections:
     NVIDIA audio driver for Linux-x86 (1.0-1)
  -> Starting install of NVIDIA audio driver for Linux-x86
  -> Checking for loaded module nvsound
  -> Checking for loaded module nvaudio
  -> License accepted.
  -> Skipping check for conflicting rpms.
  -> /proc/version is Linux version 2.6.10-2-386 (buildd@mcmurdo) (gcc version
     3.3.5 (Debian 1:3.3.5-6ubuntu1)) #1 Fri Feb 4 09:44:19 UTC 2005
  -> No precompiled kernel interface was found to match your kernel; this means
     that the installer will need to compile a new kernel interface.
  -> Kernel source path: '/lib/modules/2.6.10-2-386/build'
  -> Kernel output path: '/lib/modules/2.6.10-2-386/build'
  -> Performing cc_version_check with CC="cc".
  -> running command /bin/grep "^PATCHLEVEL ="
     /lib/modules/2.6.10-2-386/build/Makefile | /usr/bin/cut -d " " -f 3
  -> Kernel module filename is nvsound.ko
     Cleaning kernel module build directory.
     executing: 'cd ./nvsound/main; make clean'...
     rm -f *.ko *mod.* *.cmd nv*.o *~ core
  -> Building kernel module:
     executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.10-2-386/
     build SYSOUT=/lib/modules/2.6.10-2-386/build'...
     make -C /lib/modules/2.6.10-2-386/build		\
     KBUILD_SRC=/usr/src/linux-headers-2.6.10-2-386    	 KBUILD_VERBOSE=1	\
     KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1
     /nvsound/main"	\
  		   -f /usr/src/linux-headers-2.6.10-2-386/Makefile modules
     mkdir -p /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/.tmp_v
     ersions
     make -f /usr/src/linux-headers-2.6.10-2-386/scripts/Makefile.build obj=/tmp/
     selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main
  	 cc -Wp,-MD,/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/.n
     valinux.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude -Iinclude2
     -I/usr/src/linux-headers-2.6.10-2-386/include  -I/tmp/selfgz21515/NFORCE-Lin
     ux-x86-1.0-0292-pkg1/nvsound/main -Wall -Wstrict-prototypes -Wno-trigraphs -
     fno-strict-aliasing -fno-common -Os -fomit-frame-pointer -pipe -msoft-float 
     -mpreferred-stack-boundary=2 -march=i386 -I/usr/src/linux-headers-2.6.10-2-3
     86/include/asm-i386/mach-default -Iinclude/asm-i386/mach-default  -I/tmp/sel
     fgz
     21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-
     type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-
     multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DMODULE -DKBUILD_BASENAM
     E=nvalinux -DKBUILD_MODNAME=nvsound -c -o /tmp/selfgz21515/NFORCE-Linux-x86-
     1.0-0292-pkg1/nvsound/main/.tmp_nvalinux.o /tmp/selfgz21515/NFORCE-Linux-x86
     -1.0-0292-pkg1/nvsound/main/nvalinux.c
     In file included from include/linux/list.h:7,
 				 from include/linux/wait.h:23,
 				 from include/asm/semaphore.h:41,
 				 from include/linux/sched.h:18,
 				 from include/linux/module.h:10,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvalinux.c:19:
     include/linux/prefetch.h: In function `prefetch_range':
     include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
     metic
     In file included from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvalinux.c:24:
     include/asm/io.h: In function `check_signature':
     include/asm/io.h:242: warning: wrong type argument to increment
  	 cc -Wp,-MD,/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/.n
     vmixer.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude -Iinclude2 
     -I/usr/src/linux-headers-2.6.10-2-386/include  -I/tmp/selfgz21515/NFORCE-Lin
     ux-x86-1.0-0292-pkg1/nvsound/main -Wall -Wstrict-prototypes -Wno-trigraphs -
     fno-strict-aliasing -fno-common -Os -fomit-frame-pointer -pipe -msoft-float 
     -mpreferred-stack-boundary=2 -march=i386 -I/usr/src/linux-headers-2.6.10-2-3
     86/include/asm-i386/mach-default -Iinclude/asm-i386/mach-default  -I/tmp/sel
     fgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main -Wall -Wimplicit -Wretu
     rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
     no-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DMODULE -DKBUILD_BASE
     NAME=nvmixer -DKBUILD_MODNAME=nvsound -c -o /tmp/selfgz21515/NFORCE-Linux-x8
     6-1.0-0292-pkg1/nvsound/main/.tmp_nvmixer.o /tmp/selfgz21515/NFORCE-Linux-x8
     6-1.0-0292-pkg1/nvsound/main/n
     vmixer.c
     In file included from include/linux/list.h:7,
 				 from include/linux/wait.h:23,
 				 from include/asm/semaphore.h:41,
 				 from include/linux/sched.h:18,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvhw.h:16,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvmixer.c:14:
     include/linux/prefetch.h: In function `prefetch_range':
     include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
     metic
     In file included from include/linux/dmapool.h:14,
 				 from include/linux/pci.h:837,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvhw.h:22,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvmixer.c:14:
     include/asm/io.h: In function `check_signature':
     include/asm/io.h:242: warning: wrong type argument to increment
  	 cc -Wp,-MD,/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/.n
     vmain.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude -Iinclude2 -
     I/usr/src/linux-headers-2.6.10-2-386/include  -I/tmp/selfgz21515/NFORCE-Linu
     x-x86-1.0-0292-pkg1/nvsound/main -Wall -Wstrict-prototypes -Wno-trigraphs -f
     no-strict-aliasing -fno-common -Os -fomit-frame-pointer -pipe -msoft-float -
     mpreferred-stack-boundary=2 -march=i386 -I/usr/src/linux-headers-2.6.10-2-38
     6/include/asm-i386/mach-default -Iinclude/asm-i386/mach-default  -I/tmp/self
     gz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main -Wall -Wimplicit -Wretur
     n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wn
     o-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DMODULE -DKBUILD_BASEN
     AME=nvmain -DKBUILD_MODNAME=nvsound -c -o /tmp/selfgz21515/NFORCE-Linux-x86-
     1.0-0292-pkg1/nvsound/main/.tmp_nvmain.o /tmp/selfgz21515/NFORCE-Linux-x86-1
     .0-0292-pkg1/nvsound/main/nvmain.c
     In file included from include/linux/list.h:7,
 				 from include/linux/wait.h:23,
 				 from include/asm/semaphore.h:41,
 				 from include/linux/sched.h:18,
 				 from include/linux/module.h:10,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvmain.c:12:
     include/linux/prefetch.h: In function `prefetch_range':
     include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
     metic
     In file included from include/linux/dmapool.h:14,
 				 from include/linux/pci.h:837,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvhw.h:22,
 				 from /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main/nvmain.c:14:
     include/asm/io.h: In function `check_signature':
     include/asm/io.h:242: warning: wrong type argument to increment
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c: In fu
     nction `Nvaudio_mmap':
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:830: w
     arning: `remap_page_range' is deprecated (declared at include/linux/mm.h:773
     )
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:830: w
     arning: passing arg 1 of `remap_page_range' makes pointer from integer witho
     ut a cast
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:830: e
     rror: incompatible type for argument 4 of `remap_page_range'
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:830: e
     rror: too few arguments to function `remap_page_range'
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:853: w
     arning: `remap_page_range' is deprecated (declared at include/linux/mm.h:773
     )
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:853: w
     arning: passing arg 1 of `remap_page_range' makes pointer from integer witho
     ut a cast
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:853: e
     rror: incompatible type for argument 4 of `remap_page_range'
     /tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/nvmain.c:853: e
     rror: too few arguments to function `remap_page_range'
     make[4]: *** [/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/n
     vmain.o] Error 1
     make[3]: *** [_module_/tmp/selfgz21515/NFORCE-Linux-x86-1.0-0292-pkg1/nvsoun
     d/main] Error 2
     make[2]: *** [modules] Error 2
  -> Error.
  ERROR: The NVIDIA kernel module was not created.
  ERROR: Installation of the audio driver has failed.  Please see the file
  	   '/var/log/nvidia-nforce-installer.log' for details.  You may find
  	   suggestions on  fixing installation problems in the README available on
  	   the Linux driver download page at www.nvidia.com.
```
  
  
 I looked around various forums and such but I guess I'm just not bright enough to figure this one out. I'd really appreciate some help.

---

### Post by Arktis on 2005-02-05
Found a fix  [http://www.nvnews.net/vbulletin/showthread.php?t=43177]("http://www.nvnews.net/vbulletin/showthread.php?t=43177")
       
       > In linux you can simply type in: 
        NFORCE-Linux-x86-1.0-0292-pkg1.run -x
       
        Next open:
        ./NFORCE-Linux-x86-1.0-0292-pkg1/nvsound/main/Makefile.kbuild (not makefile!)
       
        goto line 54 comment the ifeq ($(REMAP_PAGE_RANGE),5)
        and on line 56 the endif so you get:
        
        #ifeq ($(REMAP_PAGE_RANGE),5)
        EXTRA_CFLAGS += -DREMAP_NEW
        #endif
        
        Next go to ./NFORCE-Linux-x86-1.0-0292-pkg1 directory and execute:
        nforce-installer
        (remember to do NOT install network card!, this patch only fixes audio!)
      
      Worked like a charm.
     
     **edit:** Grrrrrr! Except now I can't figure out how to load the dang driver. The documentation is too vague. I can't have sound in some games or in mplayer, this is just frustrating. I really need help on these final steps; the documentation nvidia gives is just too vague unless you're running some other popular distro.

---

### Post by Arktis on 2005-02-06
Okay so  doing lsmod shows me I now have these guys:
  
  soundcore               9824  4 sound,nvsound,snd
  i2c_core               21264  1 i2c_nforce2
  
  But forgive me if I don't exactly know what to do about it.
  
 There is no modules.conf which the documentation calls for, and no instructions on what to do with modules.d even though it is mentioned. It does say to do a modprobe but it doesn't give the name of what to modprobe FOR.
 
 Additional:  running dmesg gives
 
 ibm_acpi: ec object not found
 devfs_mk_dev: could not append to parent for sound/audio

---

### Post by Kevin on 2005-02-17
I tried what you posted, rebooted my computer, it beeped a couple times for some reason and then finished starting up.

I changed to OSS as the default sink in the Multimedia Systems Selector, and tried to run nvmixer.
It said there were missing libraries, so I ran:
sudo apt-get install libqt3c102-mt

I ran nvmixer again, set up my speakers and they all work now!
Hope that helps
Kevin

---

### Post by Tichondrius on 2005-02-17
[QUOTE=Arktis]Okay so  doing lsmod shows me I now have these guys:
  
  soundcore               9824  4 sound,nvsound,snd
  i2c_core               21264  1 i2c_nforce2
  
  But forgive me if I don't exactly know what to do about it.
  
 There is no modules.conf which the documentation calls for, and no instructions on what to do with modules.d even though it is mentioned. It does say to do a modprobe but it doesn't give the name of what to modprobe FOR.
 
 Additional:  running dmesg gives
 
 ibm_acpi: ec object not found
 devfs_mk_dev: could not append to parent for sound/audio[/QUOTE]
 To see all the available modules (not necessarily loaded):

$ find /lib/modules/`uname -r` 

To see just available modules whose name contains 'nv' :

$ find /lib/modules/`uname -r` | grep nv

To see all currently loaded modules:

$ lsmod

To see all cuurently loaded modules whose name contains 'nv':

$ lsmod | grep nv

To load a module:

$ sudo modprobe nvsound

Sometime you may need to update modules dependencies to get a module to load:

$ sudo depmod

---

### Post by fordp on 2005-02-17
Hello NForcers out there.

Firstly I am no Linux expert. I am an embedded software engineer for a living ;)

Anyway I am listening to Alison Moyet on my Dolby Digital Amp via Optical Spdif and NVidia drivers so I must have done something right.

First the good news is that if you have nvaudio loaded then as far as I know you have done all the hardwork.

The next suggestion I have is is Click Application->Run and type nvmixer and press enter and let me know what happens.

to those who have not got as far as getting nvaudio to load, get onto synaptic and get kernel headers for YOUR KERNEL you are running, and build-essential then download the latest nforce drivers from nvidia.com. And follow the instuctions.

I clicked the Ethernet driver off personally as the default Ubuntu one works fine and dandy.

I hope this helps.

And it plays all music not just Alison Moyet, so go for it ;)

---

### Post by aelias on 2005-04-12
[B]OK... The real problem, I think, is we can't follow the manual, provided for nVidia
becouse there is no modules.conf, neither modprobe.d/sound. So is imposible to stop the modules loaded by default by ubuntu. (we do not know where to do that)

I just compiled the driver, and if I do an lsmod, the driver appears in the list, but the problem is the same... The applications that can't access soud by ESD, fail when try to reproduce any sound.

How did you stop the AC97 driver loaded by default ?

I hope you can tell me how, By the time, I will continue listening music using xmms, with esd output support, and playing tux-racer MUTE VERSION.

thanks in advance !

;)

PD: sorry... My english sucks ! I hope you can understand me :)[/B]



[QUOTE=fordp]Hello NForcers out there.

Firstly I am no Linux expert. I am an embedded software engineer for a living ;)

Anyway I am listening to Alison Moyet on my Dolby Digital Amp via Optical Spdif and NVidia drivers so I must have done something right.

First the good news is that if you have nvaudio loaded then as far as I know you have done all the hardwork.

The next suggestion I have is is Click Application->Run and type nvmixer and press enter and let me know what happens.

to those who have not got as far as getting nvaudio to load, get onto synaptic and get kernel headers for YOUR KERNEL you are running, and build-essential then download the latest nforce drivers from nvidia.com. And follow the instuctions.

I clicked the Ethernet driver off personally as the default Ubuntu one works fine and dandy.

I hope this helps.

And it plays all music not just Alison Moyet, so go for it ;)[/QUOTE]

---

