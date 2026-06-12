---
title: "Error trying to install freenx-server"
date: 2008-10-03
forum: General Help
---

### Post by imolafem on 2008-10-03
HI all, I added the latest repos to my source.list file and ran the update.  Then I ran the install freenx command for freenx.

I got an error when I get to freenx-media, so I tried running the sudo apt-get install freenx-media install again, this is what happened:


```
amanda@kubuntu804:~$ sudo apt-get install freenx-media
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90 libaldmb1 libkdegames1 libsoup2.4-1 libfltk1.1
  libsdl-ttf2.0-0 billard-gl-data circuslinux-data libdumb1 libsdl-mixer1.2
  xaw3dg libgtkglext1 liballegro4.2 kq-data libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  freenx-media
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
8 not fully installed or removed.
Need to get 0B/24.6kB of archives.
After this operation, 81.9kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  freenx-media
Install these packages without verification [y/N]? y
(Reading database ... 112470 files and directories currently installed.)
Unpacking freenx-media (from .../freenx-media_0.7.3+svn612-0freenxteam4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/freenx-media_0.7.3+svn612-0freenxteam4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libnxredir.so.0', which is also in package freenx-server
Errors were encountered while processing:
 /var/cache/apt/archives/freenx-media_0.7.3+svn612-0freenxteam4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas?

I did already have an old (unworking version) of nx server installed.  Not sure if that's an issue or not.

---

