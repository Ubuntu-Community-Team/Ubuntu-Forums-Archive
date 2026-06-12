---
title: "fglrx-control fails to install"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by ronin69hof on 2005-09-23
Hi peeps, I dont know what I did wrong but I cannot get fglrx-control to install.  Always fails on the following error:


@reborn:~/downloads$ sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  fglrx-control xorg-driver-fglrx
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3247kB of archives.
After unpacking 10.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 85047 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin/fgl_glxgears', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking fglrx-control (from .../fglrx-control_8.8.25-0ubuntu11_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/fglrx-control_8.8.25-0ubuntu11_i386.deb (--unpack):
 trying to overwrite `/usr/share/icons/ati.xpm', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb
 /var/cache/apt/archives/fglrx-control_8.8.25-0ubuntu11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Can anyone help me out please?  

ronin

---

### Post by mlomker on 2005-09-23
> 
 trying to overwrite `/usr/X11R6/bin/fgl_glxgears', which is also in package fglrx-6-8-0


It looks like you used my how-to and already have the control panel installed.  In KDE it shows up automatically in your menu, but I've heard that it doesn't in gnome.

The control panel is /usr/X11R6/bin/fireglcontrolpanel.

---

### Post by ronin69hof on 2005-09-23
ok..now I get this error and also get the same error when trying to run fglrxinfo:

n@reborn:~/downloads$ /usr/X11R6/bin/fireglcontrolpanel
/usr/X11R6/bin/fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


ronin

---

### Post by mlomker on 2005-09-23
> /usr/X11R6/bin/fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Does the file exist?  Does **fglrxinfo** tell you that the driver is installed properly?  If you are half MESA and half ATI then things aren't going to run right.

---

### Post by ronin69hof on 2005-09-23
I get the same error when I try to run fglxrinfo and glxgears.  The file libGL.so.1 does not exist on my box.  What package do I need to install to fix it?


fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


I dont know what the heck went wrong.

ronin

---

### Post by mlomker on 2005-09-23
> fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Try running this part again:

```

su
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh

```

---

### Post by ronin69hof on 2005-09-23
now i get this:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h


think i need to start from scratch.  what exactly do i need to do to delete everything?

ronin

btw...thanks for your great help

---

### Post by mlomker on 2005-09-23
> think i need to start from scratch.  what exactly do i need to do to delete everything?


That indicates that your header files are missing.  I think you should start at [i]
Deleting the included drivers[/i] in the [how-to.](http://www.ubuntuforums.org/showthread.php?p=348911) 

Make sure to remove the **fglrx** packages in Synaptic and then do the **updatedb** process to find/remove everything else on your drive related to the drivers.

---

### Post by ronin69hof on 2005-09-23
will do

let you know how it worked out later, about ready to go home from work today.

thanks a million for your help

ronin

---

