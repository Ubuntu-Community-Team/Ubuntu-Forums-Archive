---
title: "Driver for nvidia Quadro4 XGL 580...no chance?"
date: 2008-10-30
forum: Hardware
---

### Post by distinct on 2008-10-30
Hi, 
im quite new to the forums and ubuntu, anyhow:
I looked around a bit but can't seem to find one at all, all the drivers i seem to find don't work with the card or in the documentation for them don't seem to support the Quadro4 series, only the Quadro ones.

I tried the recommended driver that was in the hardware driver list given to me on the system and clicked "activate", though that seems to only give me an error when booted.
So i uninstalled the driver this error still came up:

"Ubuntu is running in low graphics mode"
"(EE) Failed to load module "nvidia" (module does not exist, 0)"
"(EE) Drivers not available"

EDIT: Just did a search for "quadro4" in the drivers list and found the one that was initally on the system there. Installed that and it went back to the original error (i think).
> Ubuntu is running in low graphics mode

The following errors occured...may need to update...

(EE)module ABI major version (0) deosn't match server's version (1)
(EE)Failed to load mudule "glx" (module requirement mismatch, 0)
(EE)Failed to load /usr/lib/xorg/modules/drivers//ndivia_drv.so
(EE)Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers availble

I also noticed when it booted there was a [FAIL] next to the installing ot the nvidia kernel (something like that).

---

### Post by Tamlynmac on 2008-10-30
Have you tried this legacy driver from nvidia?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)

---

### Post by distinct on 2008-10-30
Ok, i downloaded the driver from:
[http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)
though i had to be logged in as root, so i used the command
"sudo -i -u root"
that logged me in as it, then executed it again...this time it required that x server wasn't running...I found this site:
[http://ubuntuforums.org/archive/index.php/t-354017.html](http://ubuntuforums.org/archive/index.php/t-354017.html)
that led me to the command "/etc/init.d/gdm stop" which killed x server and pressed CTRL+ALT->F1. Finally got into a terminal, executed it again and this time it started:
"No precompiled kernel interface was found to match your kernel; would you like the installer to attept to download a kernel interface from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)
Click Yes
Then says that theres "No matching precompiled kernel interface was found on the NVIDIA ftp site: this means that the installer will need to compile a kernel interface for your kernel."
Click Ok
"ERROR: Unable to build the NVIDIA kernel module."
Click Ok
"Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com."
Click Ok
goes back to terminal...

Given from: README
> 
INSTALLING THE KERNEL INTERFACE

The NVIDIA kernel module has a kernel interface layer that must be compiled
specifically for each kernel. NVIDIA distributes the source code to this
kernel interface layer, as well as precompiled versions for many of the
kernels provided by popular Linux distributions.

When the installer is run, it will determine if it has a precompiled kernel
interface for the kernel you are running. If it does not have one, it will
check if there is one on the NVIDIA FTP site (assuming you have an Internet
connection), and download it. If one cannot be downloaded, either because the
FTP site cannot be reached or because one is not provided, the installer will
check your system for the required kernel sources and compile the interface
for you. You must have the source code for your kernel installed for
compilation to work. On most systems, this means that you will need to locate
and install the correct kernel-source, kernel-headers, or kernel-devel
package; on some newer distributions, no additional packages are required
(e.g. Fedora Core 3, Red Hat Enterprise Linux 4).

Note that linking of the kernel interface (in the case that the interface was
downloaded or compiled at installation) requires you to have a linker
installed on your system. The linker, usually '/usr/bin/ld', is part of the
binutils package. If a precompiled kernel interface is not found, you must
install a linker prior to installing the NVIDIA driver.

Any ideas on how to install this file propally?

---

### Post by hanchung on 2008-10-30
could you post your /var/log/nvidia-installer.log ? Thanks.

---

### Post by distinct on 2008-10-30
thanks

**/var/log/nvidia-installer.log**
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Oct 30 19:30:21 2008
installer version: 1.0.7

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
  no cc version check     : false
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 96.43.07.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-7-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-7-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-7-generi
   c/build SYSOUT=/lib/modules/2.6.27-7-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -in
   clude include/linux/autoconf.h -
   Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-stric
   t-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft
   -float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i
   586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-
   default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-c
   alls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz6026/N
   VIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wsw
   itch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar
   -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -
   D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.43.07\" -UDEBUG -U_DEBU
   G -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)" 
   -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6026/NVIDIA-Linux-x86
   -96.43.07-pkg1/usr/src/nv/.tmp_nv.
   o /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1969: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv-linux.h:106:27:
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv-linux.h:108,
                    from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv-linux.h: In fun
   ction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv-linux.h:627: er
   ror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_setup_pat_entries’:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:836: warning:
   comparison between signed and unsigned
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_restore_pat_entries’:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:862: warning:
   comparison between signed and unsigned
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c: In function 
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1188: warning
   : comparison between signed and unsigned
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1191: error: 
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1195: warning
   : comparison between signed and unsigned
   /tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.c:1198: error: 
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz6026/NVIDIA-Linux-x86-96.43.07-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by hanchung on 2008-10-31
I suggest you try running these in a terminal and see what happens:

sudo apt-get install linux-restricted-modules-2.6.27-7-generic --reinstall
sudo apt-get install nvidia-glx

I suspect the Hardware Driver Utility (Jockey) installed the nvidia-glx-new instead.

If the worst comes, I will ask you to post your /etc/X11/xorg.conf, or you can edit that file yourself(run: gksudo gedit /etc/X11/xorg.conf , remember to make a copy of that file to somewhere safe like your home directory first before editing that file) by changing the (driver "nvidia") section to ("driver "nv"), the open-source driver doesn't have 3D support, but provides adequate 2D acceleration.

---

### Post by distinct on 2008-10-31
I ran these commands directly in terminal after logging in the system. As you can see i wasn't in root nor had i disabled x-server. I had no idea what the first command did after it loaded so i tried the second too. What happened? because it seems like the first one was successful and I have no idea what it actually did :/

```
ryan@Workstation:~$ sudo apt-get install linux-restricted-modules-2.6.27-7-generic --reinstall
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 764kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com intrepid/restricted linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12 [764kB]
Fetched 764kB in 5s (144kB/s)                                     
(Reading database ... 107050 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12 (using .../linux-restricted-modules-2.6.27-7-generic_2.6.27-7.12_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.27-7-generic ...
Setting up linux-restricted-modules-2.6.27-7-generic (2.6.27-7.12) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic

ryan@Workstation:~$
```

```
ryan@Workstation:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is a virtual package provided by:
  nvidia-glx-96 96.43.05-0ubuntu10
  nvidia-glx-71 71.86.04-0ubuntu10
  nvidia-glx-177 177.80-0ubuntu2
  nvidia-glx-173 173.14.12-1-0ubuntu4
You should explicitly select one to install.
E: Package nvidia-glx has no installation candidate
ryan@Workstation:~$ 
```

---

### Post by hanchung on 2008-10-31
I suggest you install: nvidia-glx-96 96.43.05-0ubuntu10
sudo apt-get install nvidia-glx-96 96.43.05-0ubuntu10

---

### Post by Elfy on 2008-10-31
afaik those are still the oild drivers and don't work with xorg if you're trying ti use intrepid

there is a beta for both 96. and 77.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by distinct on 2008-11-01
> **hanchung said:**
> I suggest you install: nvidia-glx-96 96.43.05-0ubuntu10
sudo apt-get install nvidia-glx-96 96.43.05-0ubuntu10

I tried this but it  gave me an err:
```
E: Couldn't find package...
```


> **forestpixie said:**
> afaik those are still the oild drivers and don't work with xorg if you're trying ti use intrepid

there is a beta for both 96. and 77.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I managed to install version 96 x86 this time. Though after it installed it reverted back to the black terminal. I used the command "/etc/init.d/gdm start"
```
* Starting GNOME Display Manager...            [OK] 
```
followed by "startx" as outlined in:
[http://ubuntuforums.org/archive/index.php/t-354017.html](http://ubuntuforums.org/archive/index.php/t-354017.html)

```
X: warning; process set to priority -1 instead of requested priority 0

xorg....blah blah running
...
...
...
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) No Devices detected.

Fatal Server error:
no screens found
giving up
xinit: Connection refused (errno 111): unable to connect to x server
xinit: No Such process (errno 3): Server error.
```

After reboot, the gui comes up for both loading screens but afterwards it doesn't actually load up the login screen. It displays the error...

```
Starting up ...
Loading, please wait ...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/sda5) = dev(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 8.10 Worstation tty1

Workstation login:
```

---

### Post by hanchung on 2008-11-01
sorry, my mistake, it was:
sudo apt-get install nvidia-glx-96

---

