---
title: "NVIDIA problem"
date: 2009-09-18
forum: Hardware
---

### Post by L0v3Rd0 on 2009-09-18
[LEFT]Hi !

[COLOR=Red]-------------------------------[/COLOR]
[COLOR=DarkGreen]ubuntu 9.04
 kernel 2.6.31-020631-generic[/COLOR]
[COLOR=Red]-------------------------------[/COLOR]
 I was trying to install graphics card 
  Type nvidia

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3 

from Here :  [Linux Display Driver - x86]("http://www.nvidia.com/object/linux_display_ia32_96.43.13.html")

But I have a problem when the installation

 [LEFT] 	 		 			 				No precompiled kernel interface was found to match your kernel; would you    
  like the installer to attempt to download a kernel interface for your kernel 
  from the NVIDIA ftp site ([ftp://download.nvidia.com)?]("ftp://download.nvidia.com%29/?") 			 		 	 	 
[/LEFT]
[CENTER]_[COLOR=Red]This is n[/COLOR][COLOR=Red]vidia-installer log [/COLOR]_
[/CENTER]
 
[COLOR=RoyalBlue]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Sep 18 01:55:18 2009
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
  no X server check       : true
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '3519'
   of a runnning X server.
-> Continuing per the '--no-x-check' option.
-> License accepted.
-> Installing NVIDIA driver version 96.43.13.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?]("ftp://download.nvidia.com%29?") (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:

   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.

   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").[/COLOR]          



please Help me


---
Is version 9.10 will solve the problem?  
 And automatically recognize it?

[/LEFT]

---

### Post by wojox on 2009-09-18
Check out this tutorial:

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

