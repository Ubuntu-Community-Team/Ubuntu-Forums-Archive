---
title: "CUDA detects xen kernel which I'm not using"
date: 2008-11-08
forum: General Help
---

### Post by marcog on 2008-11-08
I am trying to install the NVIDIA CUDA drivers on a fresh install of Intrepid. The version I am using is NVIDIA-Linux-x86_64-177.73-pkg2.run. It detects that I am using a xen kernel, which from some googling seems related to the xen virtual server. This halts the installer as CUDA apparently doesn't support the xen kernel. I am, however, totally unaware of running such a kernel (I have never used xen anyway). The kernel I *am* running is 2.6.27-7-generic .

Logs are below. Any bright ideas? Thanks in advance!

/var/log/nvidia-installer.log :

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Nov  8 20:11:47 2008
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
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
-> Installing NVIDIA driver version 177.73.
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
ERROR: The kernel you are installing for is a Xen kernel!
       
       The NVIDIA driver does not currently work on Xen kernels. If 
       you are using a stock distribution kernel, please install 
       a variant of this kernel without Xen support; if this is a 
       custom kernel, please install a standard Linux kernel.  Then 
       try installing the NVIDIA kernel module again.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

