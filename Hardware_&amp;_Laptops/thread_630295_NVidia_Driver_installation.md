---
title: "NVidia Driver installation"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by nimeshchandran on 2007-12-03
hello guys i installed gutsy from the alternate cd.. after that the os asked me to enable the restricted nvidi drivers and i enabled it... after that i tried to install the nvidia-glx-new driver by issuing the command sudo apt-get install nvidia-glx-new.. but it didnt work out.. the error that i got was 

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 0B/5014kB of archives.
After unpacking 15.2MB of additional disk space will be used.
(Reading database ... 84613 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.
deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4
-14.10_i386.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-
xconfig
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

by the by my graphics card is geforce 7600GS... so what should i do guys to install the driver????

---

### Post by ebe0 on 2007-12-14
Try the same with [COLOR="Red"]Synaptic Package Manager[/COLOR] after enabling all the (default) repositories. It could have been caused because of some internet connection problem.
Have a look at these : 

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)
[http://ubuntuforums.org/showthread.php?t=220835](http://ubuntuforums.org/showthread.php?t=220835)

google for [COLOR="Blue"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Please let me know if this helped

---

