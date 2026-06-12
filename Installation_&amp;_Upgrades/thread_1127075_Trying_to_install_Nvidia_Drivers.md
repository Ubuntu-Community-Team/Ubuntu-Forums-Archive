---
title: "Trying to install Nvidia Drivers"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by MatthewZ31 on 2009-04-16
I have Nivdia Geforce 8600m GT

i am using the package "NVIDIA-Linux-x86_64-100.14.09-pkg2.run"
but after using the "sudo -i" and i launch the file using the terminal, i get an error.

the error being:
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

then displays

 ERROR: Installation has failed.  Please see the file'/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

that file says;
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Apr 16 02:56:02 2009

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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5571'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).




thank you

---

### Post by sonu 1807 on 2009-04-16
Why don't you simply install it from System -> Administration -> Hardware Drivers ? After installing just reboot and it would work

---

### Post by Mark Phelps on 2009-04-16
If you press Ctrl-Alt-F2, you will get a console and can run the command from there because no X server is running then.  When done, press Ctrl-Alt-F7 or type startx to restart the Xserver.

---

### Post by MatthewZ31 on 2009-04-16
i ran in though the program using the console Ctrl-Alt-F2 and still got the error that i was running on X server.

---

