---
title: "maverick : opencl breaks compiz desktop 3d effects"
date: 2011-06-27
forum: Hardware
---

### Post by justfred on 2011-06-27
Hi,

I have an dell  Latitude E6500 laptop with an nVidia Quadro NVS 160M GPU.

I install 10.10 (i386) from scratch and made all the updates. Desktop 3d Effects (Compiz) works perfectly.

The nivdia packages installed are :

```
$ dpkg --get-selections | grep nvidia
nvidia-173-modaliases				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-current-modaliases			install 
```

When I check what packages need to be installed to have python-pyopencl, I get :

```
$ sudo apt-get install python-pyopencl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  blt dkms fakeroot freeglut3 libblas3gf libboost-python1.42.0 libgfortran3
  liblapack3gf nvidia-current nvidia-settings patch python-dateutil
  python-decorator python-matplotlib python-matplotlib-data python-numpy
  python-opengl python-pyparsing python-pytools python-tk python-tz tcl8.5
  tk8.5 ttf-lyx
Suggested packages:
  blt-demo diffutils-doc dvipng ipython python-configobj python-excelerator
  python-matplotlib-doc python-scipy python-traits texlive-extra-utils
  texlive-latex-extra python-wxgtk2.8 python-qt4 python-numpy-doc
  python-numpy-dbg python-nose libgle3 python-imaging-tk tix python-tk-dbg
  tclreadline
Recommended packages:
  nvidia-opencl-icd
The following NEW packages will be installed:
  blt dkms fakeroot freeglut3 libblas3gf libboost-python1.42.0 libgfortran3
  liblapack3gf nvidia-current nvidia-settings patch python-dateutil
  python-decorator python-matplotlib python-matplotlib-data python-numpy
  python-opengl python-pyopencl python-pyparsing python-pytools python-tk
  python-tz tcl8.5 tk8.5 ttf-lyx
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.3MB of archives.
After this operation, 130MB of additional disk space will be used.
Do you want to continue [Y/n]? n 
```

So when I finally try to install together with the recommended package "nvidia-opencl-icd", I get :

```
$ sudo apt-get install python-pyopencl nvidia-opencl-icd
[sudo] password for frederic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-opencl-icd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nvidia-opencl-icd' has no installation candidate 
```

So there seems to be an issue with the "nvidia-opencl-icd" package ...

Anyway, as I continue without the package, I get (where I highlight some of the output : especially the missing files leading to skipping the creation of other files get my attention)

```
...
Setting up tk8.5 (8.5.8-1) ...
update-alternatives: using /usr/bin/wish8.5 to provide /usr/bin/wish (wish) in auto mode.
...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
...
Setting up libblas3gf (1.2-7) ...
update-alternatives: using /usr/lib/libblas/libblas.so.3gf to provide /usr/lib/libblas.so.3gf (libblas.so.3gf) in auto mode.
...
Setting up liblapack3gf (3.2.1-8) ...
update-alternatives: using /usr/lib/lapack/liblapack.so.3gf to provide /usr/lib/liblapack.so.3gf (liblapack.so.3gf) in auto mode.

Setting up nvidia-current (260.19.06-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)

Loading new nvidia-current-260.19.06 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-28-generic-pae
Building for architecture i686
Building initial module for 2.6.35-28-generic-pae
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-28-generic-pae/updates/dkms/

depmod.......
...

```

So when I logout and log back in again, the usual compiz desktop 3d effects are off and it is impossible to get them back on through System -> Preferences -> Appearance -> Visual effects.

Also there is a new entry in System -> Administration : NVIDIA X Server Settings. However selecting this produces an error :

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

Following these instructions breaks the X server completely (Xorg.0.log) :

```
...
[    22.481] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    22.481] (EE) NVIDIA:     system's kernel log for additional error messages.
[    22.481] (II) UnloadModule: "nvidia"
[    22.481] (II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.481] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    22.481] (EE) No drivers available.
[    22.481] 
Fatal server error:
[    22.481] no screens found
[    22.481] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    22.481] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    22.481] 
```

To recover I renamed the file /etc/X11/xorg.conf to something else and reboot. The X Server starts alas as before without the Compiz Desktop 3d effects.

Any ideas on how to solve this ?

---

