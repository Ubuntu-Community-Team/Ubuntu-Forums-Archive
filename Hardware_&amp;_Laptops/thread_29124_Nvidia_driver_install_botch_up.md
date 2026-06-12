---
title: "Nvidia driver install botch up"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by nigel on 2005-04-23
Greetings all
I have made a Daft mistake I misread the instructions [here](http://www.ubuntuforums.org/showthread.php?t=3713)  and  installed the ati driver on my nvidia based system, I then (to prove my ignorance) tried the first step of installing the nvidia driver but it came up with errors, 

any help would be much appreciated

Thanks

---

### Post by Nis on 2005-04-24
What errors did you get?  With more information we'll be able to help you.

---

### Post by nigel on 2005-04-24
Well here goes

this is what happens  when i try to install the nvidia driver

```
nigel@ubuntu:/ $ sudo apt-get install nvidia-glx
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  nvidia-settings nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
Need to get 0B/2816kB of archives.
After unpacking 9351kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 63533 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.6111-1ubuntu9_i386.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia- glx' clashes with `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by fglrx -driver'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.6111-1ubuntu9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.6111-1ubuntu9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nigel@ubuntu:/ $

```

I realise I probably need to uninstall the fglrx driver, but I have no idea how

Thanks

---

### Post by Nis on 2005-04-24
```

sudo apt-get remove fglrx-driver
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```
Reboot and enjoy.

---

### Post by nigel on 2005-04-24
That worked fine, 

thanks heaps

Nigel

---

