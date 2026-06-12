---
title: "Nvidia Driver Won't Install"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by mysteriork on 2008-12-08
I recently tried to upgrade my Nvidia driver manually and when I restarted my machine I was unable to enable desktop effects.  In an effort to remove the driver and revert back to my previous state using the restricted Nvidia driver from Ubuntu, I ended up not being able to install the old ones again...

I am currently running Ubuntu 8.10

When I go to restricted drivers and try to install any of the three options (I have a Geforece 7400 Go.) it loads to about 70% then exits and does not install it.  The terminal gives the following error if I try to install through the terminal

Unpacking nvidia-177-kernel-source (from .../nvidia-177-kernel-source_177.80-0ubuntu2_i386.deb) ...
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.80-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.80-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there a way perhaps to uninstall all old Nvidia drivers and basically reinstall them from the beginning...?

Help needed...

---

