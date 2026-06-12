---
title: "GeForce 8400 GS"
date: 2008-07-10
forum: Hardware
---

### Post by Kileli on 2008-07-10
Please help this is my second attempt at resolving my video card issue. I have a GeForce 8400 GS video card i have just installed Ubuntu 8.04 on an extra hard drive. i have tried to install the nvidia drivers via envy with no effect i cannot obtain a resolution above 640x480. when i install the drive config app i cannot make any changes. I will admit i am new to linux. So if anyone would help me with a step by step walk through on how to get my graphics card to work right i would be very grateful.  i have been windows dependent for long enough its time to take control.

---

### Post by slabix on 2008-07-17
Hi, 
I also had unbelievable problems with the 8400 GS, tried everything posted everywhere in the English language, and nothing worked. Then on the French Ubuntu forums I found this post:
[http://forum.ubuntu-fr.org/viewtopic.php?id=219589](http://forum.ubuntu-fr.org/viewtopic.php?id=219589)

I'm going to paraphrase the steps becuause they worked for me. . .with a slight addition, and everying is great FINALLY.

BTW, I started with a fresh install of Hardy

a. make sure you've checked all repositories in synaptic
b. make sure you're completely updated

1.Go to synaptic, search for 'nvidia' and completely remove the currently installed  NVIDIA X.ORG driver
2.Close synaptic
3.Go to –Applications –Add/Remove, search for 'nvidia' and remove the currently installed HARDWARE DRIVERS (might not need to do this, but I'm just telling you what worked for me)
4.Go back to –Applications –Add/Remove, search for 'nvidia' and check NVIDIA BINARY X.ORG DRIVER ('NEW' DRIVER) Also check the HARDWARE DRIVERS (for GNOME unless you're using KDE)
5.Apply changes
6.Go to –System –Administration –Hardware Drivers and enable the proprietary driver for NVIDIA
7.Restart the system as ordered
8.When Ubuntu restarts, you'll probably have the stupid 640X480 resolution, but don't worry. . .here's where the real fix comes in
9.Open a terminal and type SUDO DISPLAYCONFIG-GTK
10.Choose your monitor model and desired resolution
11.At this point Ubuntu will tell you that you need to logout to restart with new settingns. Do just that. . .no need to restart. Just log out and then back in.

This fixed things for me. I tried it once in a Wubi install to make sure it worked, and then I tried it on an Ubuntu dedicated partition.

I hope this works for you. I spent about 10 days trying to figure things out before I found this solution:

Merci Beaucoup to Arkim in Marseilles. . .you saved my sanity, bud.

---

### Post by tuxxy on 2008-07-17
I have a couple models up from that card and it runs superb, also I know of people using the 8400GS too and older models fine.

According to [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) that card was compatible with even feisty.

When you installed the Ubuntu why did you use envy to install the drivers, could you not simply install them as recommnded from the r*estricted hardware drivers* in the administration menu?  I would remove the drivers and try this method as it seems to work well for nVidia cards in general even older models than yours.

---

### Post by slabix on 2008-07-17
I am also running a couple of other GeForce cards, and I have to say the 8400 GS is the only one that's caused me any trouble at all.

I don't know if it's Hardy or the card, but nothing worked the way it was supposed to, not Envy, not the manufacturer's driver, nothing.

I know how all of these installations are SUPPOSED to work, it's just that the above method is the only one that actually DID.

---

### Post by Kileli on 2008-07-17
**Special thanks to :KS[B]_Unix_Slayer_**:KS for providing this tutorial. 

I have made small changes for the aplication on ubuntu 8.04 lts
[/B]
[B]Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[/B]
**[COLOR=Red]Step 1[/COLOR]**
        [B]
In terminal window[/B]

```
sudo apt-get install build-essential
```           **Then :**

```
sudo apt-get remove nvidia*
```
**[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]**


[COLOR=DarkOrange]Step 2[/COLOR]
         [B]
In your terminal window[/B]

```
sudo /etc/init.d/gdm stop
```**Wait for the drop out of X11.**

**On your keyboard**

> Alt + <-

[COLOR=Blue]Step 3[/COLOR]

**Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver. **

**type :**

```
sudo chmod +x (/driver location/)NVIDIA-Linux-x86-173.14.09-pkg1.run
```**NVIDIA-Linux-x86-173.14.09-pkg1.run = name of the file you downloaded. If it's different, then make corrections.**


[COLOR=LightBlue]Step 4[/COLOR]

**type in :**

```
sudo sh (/driver location/)NVIDIA-Linux-x86-173.14.05-pkg1.run
```
**Follow directions on the screen.**

[COLOR=Lime]Step 5
[/COLOR]
**Reboot**, 

**Install the settings manager for NVIDIA graphics cards**  
```
sudo apt-get install nvidia-settings
```
[B]
Open settings manager with[/B]
```
sudo nvidia-settings
```**Adjust you settings, apply changes, save xorg.conf, and reboot if necessary**
Good Luck

---

### Post by adivj on 2008-07-29
Thanks Kileli! You saved me from 3 months worth of confusion and frustration! Works like a charm! :KS

---

### Post by sdennie on 2008-07-29
That guide looks good.  To add a last step, whenever the kernel updates, the new kernel will not have the nvidia driver so, when you boot into it, you will be back in low graphics.  To prevent that, you can use this guide: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by adivj on 2008-08-29
Hi again, pardon the newbie-ness.
Had to reformat my hard drive (Vista issues...). Then reinstalled Ubuntu, then tried this again, everything went okay, up till the point where it was building the kernel module. Then i got this error: "Unable to build NVIDIA kernel module". Can anyone offer some assistance? 

Here's my installer log file thingie:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Aug 29 18:14:09 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-19-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvacpi.
   o nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvacpi.o nvidi
   a.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-gener
   ic/build SYSOUT=/lib/modules/2.6.24-19-generic/build'...
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.24-19-generic/build /lib/modules
   /2.6.24-19-generic/build cc_sanity_check full_output
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.24-19-generic/build /lib/modules
   /2.6.24-19-generic/build select_makefile full_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS
   =/tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/.tmp_ve
   rsions ; rm -f /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/.
   tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz11224/NVIDIA-Linux-x86-100.14.
   09-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz11224/NV
   IDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/.nv
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclu
   de/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdecl
   aration-after-statement -Wno-pointer-sign   -I/tmp/selfgz11224/NVIDIA-Linux-
   x86-100.14.09-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wform
   at -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror 
   -O 
   -fno-common -msoft-float          -MD   -Wsign-compare -Wno-cast-qual -Wno-e
   rror -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_VERSION_STRING
   =\"100.14.09\" -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIP
   LE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COU
   NT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_I
   NSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_
   PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_ACQUIRE_CONSOLE_SEM_PRESENT -DNV_
   VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
   nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz11224/NVIDIA-Li
   nux-x86-100.14.09-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz11224/NVIDIA-Linux-x8
   6-100.14.09-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/s
   rc/nv/nv-linux.h:78,
                    from /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c: In functio
   n ‘__nv_setup_pat_entries’:
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:946: warnin
   g: comparison between signed and unsigned
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c: In functio
   n ‘__nv_restore_pat_entries’:
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:972: warnin
   g: comparison between signed and unsigned
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c: In functio
   n ‘nv_kern_cpu_callback’:
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1278: warni
   ng: comparison between signed and unsigned
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1285: warni
   ng: comparison between signed and unsigned
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c: In functio
   n ‘nvidia_init_module’:
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1322: error
   : too many arguments to function ‘kmem_cache_create’
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1431: error
   : too many arguments to function ‘kmem_cache_create’
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1567: error
   : void value not ignored as it ought to be
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c: In functio
   n ‘nvidia_exit_module’:
   /tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv.c:1599: error
   : void value not ignored as it ought to be
   make[3]: *** [/tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/src/nv/nv
   .o] Error 1
   make[2]: *** [_module_/tmp/selfgz11224/NVIDIA-Linux-x86-100.14.09-pkg1/usr/s
   rc/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by sdennie on 2008-08-29
Is there a reason you went with a driver that old?  It may not be compatible with such a new kernel.  I would get the latest drivers from: [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by adivj on 2008-08-30
> Is there a reason you went with a driver that old?

I didn't check properly...man... haha!  Yes, got the latest driver and everything worked, as it did before, like a charm. 

Not the most defining moment in my life... But thanks a bunch for pointing that out.

---

### Post by sdennie on 2008-08-30
Glad it worked.  As a side note, I just started testing the latest beta driver (177.70) on my 8400M GS and the performance is excellent with this guide: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088).  I also use this guide with mine: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369).  It remains to be seen if suspend/resume will work consistently with the new driver but, performance really is quite good.

---

### Post by AeroTITAN on 2008-12-30
This is by far the most comprehensive tutorial I have found, so thanks!

My problem is I can't boot up ubuntu 8.10 with the new 8400 gs card already physically in the tower.  As such, the driver won't install because it doesn't see the hardware.  I also can't boot in Recovery Mode.  The closest I came was having both graphics cards in at the same time, but the login screen would totally freeze after entering my password.  This only worked a few times and now I'm back to Seg faults.

The graphics card is good.  It works very well in Windows.

And lastly, I cannot boot from the LiveCD - it freezes at the same spot as the regular boot menu does.

Hardware:  HP a749c, geforce 8400 gs, 2GB DDR SDRAM, XP SP3 dual boot with Ubuntu 8.10

Any ideas?

---

