---
title: "Problem removing - installing nvidia driver"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by whosmatt on 2009-03-04
I did the nvidia -> ATI ->back to nvidia switch and now I can't get the nvidia driver going. I was messing around and installed nvidia-glx when what i really need is nvidia-glx-new (i think). anyway, now i get this:

```

root@esi-131-ubuntu:/var/lib/dpkg/info# apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9372kB of archives.
After this operation, 28.3MB of additional disk space will be used.
(Reading database ... 131881 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_169.12+2.6.24.16-23.56_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.16-23.56_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.16-23.56_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have searched the forums and tried some solutions but nothing has helped me.  Anybody know what i should do?

FYI i have tried clearing out the contents of /usr/lib/nvidia/ to no avail.

---

