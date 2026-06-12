---
title: "/var/log/nvidia-installer-log Problems installing the drivers for NVIDIA-GOFX 256meg"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by tkeisling on 2005-08-17
Specs on laptop: Dell Precision M70
Nvidia gofx 256 meg video card.

I'm getting this error when I try to sh Nvidia*:

    license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6


OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> No precompiled kernel interface was found to match your kernel; would you li   ke the installer to attempt to download a kernel interface for your kernel f   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/usr/src/linux'

-> Kernel source path: '/usr/src/linux'
-> Performing CC test with CC="cc".
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.

       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


How do I fix this? :)

---

### Post by s_p_a_r_k_y on 2005-08-17
you need the kernel source package. do you have a /usr/src/linux directory? if not use synaptic to get the kernel source and headers which correspond do your kernel version.

```
uname -a
``` to get your kernel version

---

### Post by tseliot on 2005-08-17
You can try my guide, it's easy:

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

---

### Post by tkeisling on 2005-08-17
-After doing what you had said i got farther along in the installation, but then this happened. 


ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.

> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   cs: IO port probe 0x0a00-0x0aff: clean.
   wlan0: no IPv6 routers present
   eth0: no IPv6 routers present
   ibm_acpi: ec object not found
   cdrom: open failed.
   cdrom: open failed.
   cdrom: open failed.
   cdrom: open failed.
   UDF-fs: No VRS found
   ISO 9660 Extensions: Microsoft Joliet Level 3
   ISO 9660 Extensions: RRIP_1991A
   UDF-fs: No VRS found
   ISO 9660 Extensions: Microsoft Joliet Level 3
   ISO 9660 Extensions: RRIP_1991A
   nvidia: version magic '2.6.10-5-386 preempt 386 gcc-3.4' should be
   '2.6.10-5-386 preempt 386 gcc-3.3'
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
                                                                    317,4         Bot

---

### Post by tkeisling on 2005-08-17
I did uname -r and 2.6.10-5-386
 came up so i opened synaptic and installed that.

---

### Post by tseliot on 2005-08-17
Before running NVIDIA installer, type:

CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

export CC

If this doesn't work try with gcc-3.3 (substitute it in the line above) and start nvidia installer again

---

### Post by tseliot on 2005-08-17
Of course make sure you have both gcc 3.3 and 3.4 installed in synaptic (not only th "base" package)

---

### Post by tkeisling on 2005-08-17
I had to change the version to gcc 3.3 because thats what was used to compile my kernel and it worked, woot thanks for the help.

---

