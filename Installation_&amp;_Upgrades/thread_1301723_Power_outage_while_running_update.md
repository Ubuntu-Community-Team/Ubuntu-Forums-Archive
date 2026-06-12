---
title: "Power outage while running update"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by phatbastard on 2009-10-26
I had a power outage while running a update and now my system will not update and cannot load nvidia module. I have tried the --configure -a option with no luck. Here are my errors

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gstreamer0.10-plugins-bad kvm linux-generic linux-headers-generic
  linux-image-generic mplayer-skin-blue
The following packages will be upgraded:
  nvidia-glx-185 software-center
2 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
12 not fully installed or removed.
Need to get 0B/16.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: triggers ci file contains unknown directive `Package:'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by TenPlus1 on 2009-10-26
sudo apt-get remove nvidia-glx-185

reboot and run Hardware Drivers again to re-install your gfx card...

---

### Post by phatbastard on 2009-10-27
I think apt-get is broken. This is the error i get if i try to install or remove anything.

dpkg: triggers ci file contains unknown directive `Package:'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

