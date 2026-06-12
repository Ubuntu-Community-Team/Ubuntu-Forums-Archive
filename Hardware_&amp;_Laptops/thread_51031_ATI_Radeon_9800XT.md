---
title: "ATI Radeon 9800XT"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by tbasten on 2005-07-22
I just got myself an ATI radeon 9800XT today and replaced my old one (Gefore 4 mx 440) Now my machine was configured to run my nvidia card. I have download the drivers for my card from the ATI website. I installed it and did everything else. i can start x (i edited my xorg.conf so it loaded fglrx instead of nvidia)

Now when i go glxgear i get 
```
tbasten@Dyna:~ $ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.

```

So i thought i might try uninstalling nvidia-glx i got the following

```
tbasten@Dyna:~ $ sudo dpkg -P nvidia-glx
(Reading database ... 97771 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/libGL.so.1' with
  different file `/usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx

```

Can someone help me please. If you need more details to tell me

---

### Post by tbasten on 2005-07-22
I downloaded the rpm off ati support, then i converted it to deb, i tryed to install it and i got this error msg,

tbasten@Dyna:~ $ sudo dpkg -i fglrx-6-8-0_8.14.13-2_i386.deb
(Reading database ... 97766 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.14.13-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.14.13-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.14.13-2_i386.deb

any ideas. ](*,)

---

### Post by Atomic on 2005-07-22
Install the linux kernel headers that fit your architecture via synaptic.
this will work - did it 1 h ago ;-)

---

### Post by tbasten on 2005-07-22
tbasten@Dyna:~ $ sudo apt-get install linux-kernel-headers
Reading package lists... Done
Building dependency tree... Done
linux-kernel-headers is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by black hole sun on 2005-07-22
[QUOTE=tbasten]I downloaded the rpm off ati support, then i converted it to deb, i tryed to install it and i got this error msg,

tbasten@Dyna:~ $ sudo dpkg -i fglrx-6-8-0_8.14.13-2_i386.deb
(Reading database ... 97766 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.14.13-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.14.13-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-6-8-0_8.14.13-2_i386.deb

any ideas. ](*,)[/QUOTE]
change the command to

sudo dpkg -i --force-all fglrx-6-8-0_8.14.13-2_i386.deb

This is safe, and it's very necessary, since the ati driver must use its own opengl library, not the one from the mesa project.

But yes, you also need your kernel headers installed.

---

### Post by tbasten on 2005-07-22
```
tbasten@Dyna:~ $ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3185kB of archives.
After unpacking 10.2MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 97904 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tbasten on 2005-07-22
Its ok i got it installed. Now i cant get direct rendering enabled

tbasten@Dyna:~ $ glxinfo | grep 'rendering'
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
tbasten@Dyna:~ $

---

### Post by black hole sun on 2005-07-22
[QUOTE=tbasten]Its ok i got it installed. Now i cant get direct rendering enabled

tbasten@Dyna:~ $ glxinfo | grep 'rendering'
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
tbasten@Dyna:~ $[/QUOTE]
 Use the one from the ati site not from the ubuntu repos. That one is an ancient version.

---

