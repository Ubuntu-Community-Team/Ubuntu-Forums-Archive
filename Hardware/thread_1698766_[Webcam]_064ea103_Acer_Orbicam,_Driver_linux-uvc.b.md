---
title: "[Webcam] 064e:a103 Acer Orbicam, Driver linux-uvc.berlios"
date: 2011-03-02
forum: Hardware
---

### Post by burroparda on 2011-03-02
Hi all,
hope someone can help me, since on the italian ubuntu forum no one has been able to answer me!

My Acer Emachines E525 has got an ArcerOrbicam 064e:a103 supported by [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download)
I followed their link [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) (commands in "Basic approach") for installing the driver, but it gave me this error:

```

linda@linda-eMachines-E525:~$ git clone git://linuxtv.org/media_build.git
fatal: destination path 'media_build' already exists and is not an empty directory.
linda@linda-eMachines-E525:~$ cd media_build 
linda@linda-eMachines-E525:~/media_build$ ./build.sh
************************************************************
* This script will download the latest tarball and build it*
* Assuming that your kernel is compatible with the latest  *
* drivers. If not, you'll need to add some extra backports,*
* ./backports/<kernel> directory.                          *
* It will also update this tree to be sure that all compat *
* bits are there, to avoid compilation failures            *
************************************************************

Note: requires git/perl/make/gcc/patch/perl-Digest-SHA1/patchutils packages to work
git pull git://linuxtv.org/media_build.git master
From git://linuxtv.org/media_build
 * branch            master     -> FETCH_HEAD
Already up-to-date.
make -C linux/ download
make: Entering directory `/home/linda/media_build/linux'
wget http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5 -O linux-media.tar.bz2.md5.tmp
--2011-02-26 21:23:08--  http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5
Resolving linuxtv.org... 130.149.80.248
Connecting to linuxtv.org|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 93 [application/x-bzip2]
Saving to: `linux-media.tar.bz2.md5.tmp'

100%[======================================>] 93          --.-K/s   in 0s      

2011-02-26 21:23:09 (9.84 MB/s) - `linux-media.tar.bz2.md5.tmp' saved [93/93]

make: Leaving directory `/home/linda/media_build/linux'
make -C linux/ untar
make: Entering directory `/home/linda/media_build/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied
make: Leaving directory `/home/linda/media_build/linux'
make
make -C /home/linda/media_build/v4l 
make[1]: Entering directory `/home/linda/media_build/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/linda/media_build/v4l/firmware'
make[2]: Leaving directory `/home/linda/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/linda/media_build/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/linda/media_build/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/linda/media_build/linux'
Applying patches for kernel v2.6.35
patch -s -f -N -p1 -i ../backports/v2.6.37_dont_use_alloc_ordered_workqueue.patch
patch -s -f -N -p1 -i ../backports/v2.6.36_input_getkeycode.patch
patch -s -f -N -p1 -i ../backports/v2.6.35_vm_prev.patch
patch -s -f -N -p1 -i ../backports/v2.6.35_firedtv_handle_fcp.patch
patch -s -f -N -p1 -i ../backports/v2.6.35_i2c_new_probed_device.patch
patch -s -f -N -p1 -i ../backports/v2.6.35_work_handler.patch
make[2]: Leaving directory `/home/linda/media_build/linux'
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/linda/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/linda/media_build/v4l/bttv-input.o
  CC [M]  /home/linda/media_build/v4l/cx18-alsa-main.o
  CC [M]  /home/linda/media_build/v4l/cx18-alsa-pcm.o
  CC [M]  /home/linda/media_build/v4l/cx18-driver.o
  CC [M]  /home/linda/media_build/v4l/cx18-cards.o
  CC [M]  /home/linda/media_build/v4l/cx18-i2c.o
  CC [M]  /home/linda/media_build/v4l/cx18-firmware.o
  CC [M]  /home/linda/media_build/v4l/cx18-gpio.o
  CC [M]  /home/linda/media_build/v4l/cx18-queue.o
  CC [M]  /home/linda/media_build/v4l/cx18-streams.o
  CC [M]  /home/linda/media_build/v4l/cx18-fileops.o
  CC [M]  /home/linda/media_build/v4l/cx18-ioctl.o
  CC [M]  /home/linda/media_build/v4l/cx18-controls.o
  CC [M]  /home/linda/media_build/v4l/cx18-mailbox.o
  CC [M]  /home/linda/media_build/v4l/cx18-vbi.o
  CC [M]  /home/linda/media_build/v4l/cx18-audio.o
  CC [M]  /home/linda/media_build/v4l/cx18-video.o
  CC [M]  /home/linda/media_build/v4l/cx18-irq.o
  CC [M]  /home/linda/media_build/v4l/cx18-av-core.o
  CC [M]  /home/linda/media_build/v4l/cx18-av-audio.o
  CC [M]  /home/linda/media_build/v4l/cx18-av-firmware.o
  CC [M]  /home/linda/media_build/v4l/cx18-av-vbi.o
  CC [M]  /home/linda/media_build/v4l/cx18-scb.o
  CC [M]  /home/linda/media_build/v4l/cx18-dvb.o
  CC [M]  /home/linda/media_build/v4l/cx18-io.o
  CC [M]  /home/linda/media_build/v4l/cx23885-cards.o
/home/linda/media_build/v4l/cx23885-cards.c:28: fatal error: staging/altera.h: No such file or directory
compilation terminated.
make[3]: *** [/home/linda/media_build/v4l/cx23885-cards.o] Error 1
make[2]: *** [_module_/home/linda/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/linda/media_build/v4l'
make: *** [all] Error 2
*** ERROR. Aborting ***
linda@linda-eMachines-E525:~/media_build$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
linda@linda-eMachines-E525:~/media_build$

```Error at the first line: [COLOR=red]linda@linda-eMachines-E525:~$ git clone git://linuxtv.org/media_build.git
fatal: destination path 'media_build' already exists and is not an empty directory.[/COLOR]
and at the end:  [COLOR=red]cx23885-cards.o[/COLOR]:
[COLOR=red]CC [M]  /home/linda/media_build/v4l/cx23885-cards.o
/home/linda/media_build/v4l/cx23885-cards.c:28: fatal error: staging/altera.h: No such file or directory
compilation terminated.[/COLOR]

At the end it says to eliminate [COLOR=red]linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic[/COLOR] Is the case to do that?
Many thanks.
Linda

---

### Post by Akriss on 2011-03-02
Hiya,

Its funny, right now I'm in the middle of trying to build V4L-DVB. And as you ran in to this. 
but taking a clue from the page  [How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") 

Theres a note about ubuntu and having to edit another file, I just applied the same to the error files I had(I say fileS because there where a few). 

It seems to have worked.

Now, being that I'm a Linux noob I have no idea what thats going to break. =/  so please tread lightly :)

---

