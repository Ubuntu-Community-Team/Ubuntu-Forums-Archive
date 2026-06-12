---
title: "DJ Control MP3 / Mixxx / ubuntu 9.04"
date: 2009-05-20
forum: Hardware
---

### Post by dharmagio on 2009-05-20
hello

hi need help to put this hercules dj control mp3 to work with mixxx

hi readed a lot of info but not being able to work on my Ubuntu 9.04

the first thing i have to install i know its the drivers released recently by Hercules, they were tested with Ubuntu 8.10 but not sure if they work with the new version so thats my doubt.

what i did was download the driver from,

[http://ts.hercules.com/eng/index.php?pg=view_files&gid=2&fid=28&pid=179&cid=1](http://ts.hercules.com/eng/index.php?pg=view_files&gid=2&fid=28&pid=179&cid=1)

Hercules_DJSeries_Linux.tgz

after download this file hi uncompress it and installed this 2 packages in pachage installer, one is the kernel module "hdjmod-dkms_1.28_all.deb" and other the control panel "hdjcpl_1.09-1_i386.deb"

after the install a icon appears in menu "hercules dj control panel"
when i run it, appear a simple window informing:

hercules dj control panel
please plug your hercules dj product
package: hdjcpl-1.09-1
control panel: 1.09

but i allready have the usb cable connected i restarted but nothing different happends. so its not deteting the console.

then i installed correctly mixxx-1.6.1+Herc from source and its running fine but without the hercules midi controller working of course.

so any body know what might be the problem? an answer to this might help many people i think, thanks.

---

### Post by dharmagio on 2009-05-20
this is the detailed kernel module install
______________________________________________________________________
fil@fil-laptop:~/Desktop$ sudo dpkg -i hdjmod-dkms_1.28_all.deb
Selecting previously deselected package hdjmod-dkms.
(Reading database ... 155657 files and directories currently installed.)
Unpacking hdjmod-dkms (from hdjmod-dkms_1.28_all.deb) ...
Setting up hdjmod-dkms (1.28) ...
Loading new hdjmod-1.28 DKMS files...

Loading tarball for module: hdjmod / version: 1.28

Loading /usr/src/hdjmod-1.28...
Creating /var/lib/dkms/hdjmod/1.28/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-11-generic -C /lib/modules/2.6.28-11-generic/build M=/var/lib/dkms/hdjmod/1.28/build.....
cleaning build area....

DKMS: build Completed.
Installing module...

hdj_mod.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-11-generic/updates/dkms/

Running post_install:

depmod....

DKMS: install Completed.

______________________________________________________________________
this is the detailed control panel install
______________________________________________________________________

fil@fil-laptop:~/Desktop$ sudo dpkg -i hdjcpl_1.09-1_i386.deb
Selecting previously deselected package hdjcpl.
(Reading database ... 155658 files and directories currently installed.)
Unpacking hdjcpl (from hdjcpl_1.09-1_i386.deb) ...
Setting up hdjcpl (1.09-1) ...

---

### Post by RadiatorNinjaen on 2009-09-23
I just wanted to say that I have the same problem. To me, it seems like the driver only works on the standard kernel and not the real-time kernel from Ubuntu Studio. Are you using Ubuntu Studio?

This is what happened to me, with a Hercules RMX:

1. I had Ubuntu Studio 9.04 on one machine, with the RT kernel. Same problem as above, driver seemed to install but did not detect the RMX.
2. Tried it on another machine with Eeebuntu 3.0 (= 9.04, not RT) and it worked perfectly.
3. Downgraded the first machine to Ubuntu Studio 8.10 (that has no RT kernel). Once I had installed the driver I noticed that after restarting, just after the loading screen I would see text on the screen for a few seconds, that the machine was doing something with the driver I just installed. Then go to the login. This also worked perfectly.
4. I then tried to downgrade the first machine again, this time to Ubuntu Studio 8.04, that has a RT kernel. Once again, this did not work.

Now, obviously, it seems to me like the driver just won't work with the RT kernel. If you look at [the page for the Linux driver from Hercules]("http://ts.hercules.com/eng/index.php?pg=view_files&gid=2&fid=28&pid=215&cid=1") (it's in the bottom), it states somewhere that "3) In general, the distribution should be set up in order to compile kernel modules (Notes 1 and 2 above ensure this for Fedora and OpenSuse, and the other cited distributions should be immediately ready)." and I think it might have something to do with that.

I'm wondering if maybe:

1) The RT kernel is not setup to compile kernel modules. How do I know? Do I need to install some packages to enable it?
2) Hercules made the driver in a way such that it only works with the normal kernel and not the RT.

Any help would be greatly appreciated, as currently you apparently cannot use this DJ console with the real-time kernel. :)

---

### Post by RadiatorNinjaen on 2009-09-24
Just wanted to let others know that I finally got it to work with my Hercules RMX. Here goes:

1. I installed the normal version of Ubuntu 9.04.
2. Installed the driver in the normal kernel (probably not necessary).
3. I then installed the real-time kernel with headers and dkms - packages dkms, linux-rt, linux-rt-headers-[kernel version].
4. Rebooted and loaded the rt kernel from grub at startup.
5. Installed the driver again, while running the rt kernel.
6. Rebooted and loaded the rt kernel once again at startup.
7. Win.

It seems that Ubuntu includes something needed for the kernel module driver to install that Ubuntu Studio does not include. I have no idea what. If somebody has, please let us know. :)

---

### Post by kmannarbor on 2011-12-27
Trying to get my Hercules DJ Control RMX up and running in the latest build of Ubuntu. Installed pre the instructions on the hercules site. Got the control panel up but when I plug in the controller, nothing happens. Also, when I try to install hdjmod-dkms.deb I get the following error:
Selecting previously deselected package hdjmod-dkms. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 159446 files and directories currently installed.) 
Unpacking hdjmod-dkms (from .../hdjmod-dkms_1.28_all.deb) ... 
Setting up hdjmod-dkms (1.28) ... 
Loading new hdjmod-1.28 DKMS files... 
 
Loading tarball for hdjmod-1.28 
 
DKMS: ldtarball completed. 
 
Creating symlink /var/lib/dkms/hdjmod/1.28/source -> 
                 /usr/src/hdjmod-1.28 
 
DKMS: add completed. 
Installing prebuilt kernel module binaries (if any) 
Building module... 
 
Kernel preparation unnecessary for this kernel.  Skipping... 
 
Building module: 
cleaning build area.... 
make KERNELRELEASE=3.0.0-14-generic -C /lib/modules/3.0.0-14-generic/build M=/var/lib/dkms/hdjmod/1.28/build......(bad exit status: 2) 
ERROR (dkms apport): binary package for hdjmod: 1.28 not found 
Error! Bad return status for module build on kernel: 3.0.0-14-generic (i686) 
Consult /var/lib/dkms/hdjmod/1.28/build/make.log for more information. 
dpkg: error processing hdjmod-dkms (--install): 
 subprocess installed post-installation script returned error exit status 10 
Errors were encountered while processing: 
 hdjmod-dkms 


Any ideas what might be going wrong? New to Linux.

Thanks in advance,

kmannarbor

---

