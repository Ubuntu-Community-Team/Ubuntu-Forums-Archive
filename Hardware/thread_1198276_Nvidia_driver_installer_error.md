---
title: "Nvidia driver installer error"
date: 2009-06-27
forum: Hardware
---

### Post by yds753 on 2009-06-27
Hi,
I've been using ubuntu for a year now, and recently I upgraded to the newest ubuntu-version, which gave a conflict with the nvidia-drivers, so I decided to reinstall the whole thing.  I am currently running kernel 2.6.28-13-generic,
and when I try to install NVIDIA-Linux-x86-177.80-pkg1.run  for my Nvidia quadro 770M card, the installer gives an error.  Here is the log file of the installer:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jun 27 14:33:46 2009
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
-> Installing NVIDIA driver version 177.80.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-13-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-13-generic/build'
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
       driver download page at www.nvidia.com.
```

I have really no clue, as the kernel headers are installed correctly (I even reinstalled them).
Does anybody know how to solve this problem?
Thanks in advance!

---

### Post by Hobgoblin on 2009-06-27
Why are you installing manually, doesn't **System > Administration > Hardware drivers** give you the option to enable the Nvidia driver?

---

### Post by yds753 on 2009-06-30
Unfortunately, that doesn't work. (there is no option to enable the nvidia drivers).  I also tried it with envy, but with no success.
I am currently working with the generic vga drivers, but the screen resolution is very limited.

---

