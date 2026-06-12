---
title: "[SOLVED] Nvidia drivers installation errors"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2008-12-15
Hi,

I'm trying to install nvidia drivers for my card.  I've done it before on other systems but now I'm trying it on Crunchbang linux (ubuntu based, uses openbox).  

I use ctrl+alt+f3, stop gdm, start the installer.  It starts, it notifies me no matching kernel things were found, I say search for one, it searches, then gives me an error.

First, the error was "cannot find the package binutils, please make sure its installed."

I installed it, but I got another similar error.  It couldn't find "gcc".  Then the same thing but with the package "make".  Then again with something like "kernel source tree".

Can someone please tell me what's wrong?  Thanks.  
Here's my installer-log from /var/log (scroll to the bottom and see the first error, that is the error I keep getting with different things:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Dec 15 16:12:42 2008
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
-> Installing NVIDIA driver version 177.82.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Partyboi2 on 2008-12-15
Open a terminal and install build-essential and linux headers
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by celtic426 on 2008-12-16
thank you, that worked!

---

