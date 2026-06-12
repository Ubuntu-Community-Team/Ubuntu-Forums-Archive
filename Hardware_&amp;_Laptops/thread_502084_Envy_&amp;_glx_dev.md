---
title: "Envy &amp; glx dev"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by ibachar on 2007-07-16
Hi,

I have Ubuntu 7.04 installed and I use the envy script to install my GeForce 6200 drivers.
the problem is the script does not install the glx-dev package so i can't compile OpenGL
programs and when I try to install glx-dev it gives me this massage:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  nvidia-glx-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/156kB of archives. After unpacking 823kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 163502 files and directories currently installed.)
Unpacking nvidia-glx-dev (from .../nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-16.29_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so to /usr/lib/nvidia/libGL.so.xlibmesa by nvidia-glx-dev' clashes with `diversion of /usr/lib/libGL.so to /usr/lib/nvidia/libGL.so.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-16.29_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Any clue?

---

### Post by ibachar on 2007-07-16
Fixed.

Just created the symlink myself.

---

