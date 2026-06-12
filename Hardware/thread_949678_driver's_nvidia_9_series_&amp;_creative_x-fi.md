---
title: "driver's nvidia 9 series &amp; creative x-fi"
date: 2008-10-16
forum: Hardware
---

### Post by aircos on 2008-10-16
hellow , 

iam useing ubuntu 8.04 hardy

i'f been reading ALOT about the creative x-fi extreme gamer and discoverd there are stil no driver's for it to run on linux (only some beta drivers upon u gota install whit oss wich is out of my skill range so waiting for newer driver's and meanwhile useing my onboard card wich is lower quality bhut heck better than no sound , if somebody could gimme a nice step bye step guid on howto get my x-fi going i'd love to hear it tho)

and my geforce 9 card ( g9800X2 ) i got the driver's from nvidia wich comes whit a run file " NVIDIA-Linux-x86_64-177.80-pkg2.run " bhut when i go to the folder lock and star the setup the setup loads up untill some dos looking thingy is telling me iam running x so this is what it tells me
 
ERROR: You appear to be running an X server; please exit X before installing.For further details, please see the section INSTALLING        THE NVIDIA DRIVER in the README available on the Linux driver         download page at [www.nvidia.com](www.nvidia.com).

 whit a ok button wich leads to 

ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

so i lookedup the log wich give me this

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Oct 16 18:15:49 2008
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5839'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

anybody abel to help me out? 
(srry iam a linux noob and evrything i get working on my pc is from reading forums on how peeps solved there problems bhut i cant program personaly wich is why i kinda am stuck when there is no step bye step guide) btw how do i see iam useing the 64bit version??? cant seem to find it iam guesing i am useing the 64bit bhut iam not sure of that ](*,):lolflag:

---

