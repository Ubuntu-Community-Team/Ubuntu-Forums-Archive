---
title: "Cannot get Logitech quickcam drivers to work."
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by the_it on 2005-12-14
hi!  I'm trying to get logitech quickcam drivers to work out for my ubuntu box (breezy badger 5.10 with kernel 2.6.12-10).  I did find drivers, but I can't get them to compile.  I was wondering if you guys could help me out.

First, the model of the cam.  Here's the output of lsusb

```
Bus 001 Device 003: ID 046d:d001 Logitech, Inc. QuickCam Pro
```

I checked up on the other webcam threads and there are drivers for the pwc / spca modules for linux.  However, the product ids supported for 850 something and 900 something.  I did an long searching for drivers on the net for the d001 product id, and I was able to find this nw802 kernel module.  This is from
nw802.sourceforge.net

Unfortunately, the kernel module was designed for 2.4 kernels, and I'm stuck with a 2.6 kernel.  Downgrading is not an option, though I did note that the developer provided initial 2.6 kernel support.  The developer provided a patch for 2.6 kernels, unfortunately I can't get it to work.

```
New files in the CVS.

Patch for kernel 2.6 and a Makefile for 2.6. And some small bugg fixes.
So to compile with a 2.6 kernel :

cvs -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802 login
cvs -z3 -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802
co nw802-2.4
cd nw802-2.4
cp Makefile.26 Makefile
patch -p0 < patch-2.6
make clean
make
```

This code requires that you get the cvs version of the driver (which I did) and then apply the patch (which I did).  I downloaded the files from cvs and applied the patch.

Here's my terminal output:
```
dilnet@dlntbldr:~/nw802-2.4$ ls
Changelog         Makefile              nw802.init       README
cvideopro.init    Makefile.26           nw8xx_jpgl.c     SpaceCam.init
d-link-350c.init  mustek_300_mini.init  nw8xx_jpgl.h     trust_space.init
DS3303u.init      nw800.init            nw8xx_regedit.c  Twinkle.init
kritter.init      nw801.init            patch-2.6        usbvideo.c
LICENSE           nw802.c               proscope.init    usbvideo.h
dilnet@dlntbldr:~/nw802-2.4$ cp Makefile.26 Makefile
dilnet@dlntbldr:~/nw802-2.4$ patch -p0 < patch-2.6
patching file nw802.c
Hunk #10 succeeded at 770 with fuzz 2.
dilnet@dlntbldr:~/nw802-2.4$
```

applying the patch seems to be successful.  All that's left now is to compile.  I did read the README, which said to define my cam model from the nw8xx_regedit.c file.  At the start of the file there is a #define which you can change to define either nw800, nw801, or nw802.  To my knowledge (though I have yet to verify) my cam is supposed to be the nw802 model (which is the default define), so I don't have to change anything.

Here's the howto line in the README
```
 NW802 kernel module
=====================

This kernel module is a driver for USB webcam based on the DivIO chipsets NW800/NW801/NW802.

This version is an hybrid version. It includes the almost latest code for image decoding ( which is REALLY faster and has a REALLY improved quality of image ) and the old ( almost obsolete ) usb/cam interaction core.

Due to the limitation of this cam control module, support is limited but this version does include some /proc interface that allows tweaking the cam registers 'on-the-fly' which allows to do tests and more important tweak some image register. For this, a handy GTK utils ( nw8xx_regedit ) is now provided.


How to use it ?
---------------

* Edit nw8xx_regedit.c, at the start there is some #define to choose your cam chip ( registers differs and the GTK utils doesn't do any autodetect ).
* Type :
 # make
 # su
 # modprobe videodev
 # insmod usbvideo.o
 # insmod nw802.o
* Launch xawtv ( or any V4L compatible app. Since the driver currently ignores quite a lot of V4L request like videosize, format, ... the app may give warning or refuses to work at all ... xawtv works, newer version of gnomemeeting don't ... )
```

Here's the start of the nw8xx_regedit.c file
```
#define NW802_MODEL
//#define NW801_MODEL
```
Again, since I assumed i have an nw802 cam I didn't have to change anything.  Even if I had the wrong cam, I still should be able to compile, right?

After that, I type in make.  Here's what happens:
```
dilnet@dlntbldr:~/nw802-2.4$ make
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.h .
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.c .
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/dilnet/nw802-2.4/nw8xx_jpgl.o
In file included from /home/dilnet/nw802-2.4/nw8xx_jpgl.c:38:
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:43:22: usbvideo.h: No such file or directory
In file included from /home/dilnet/nw802-2.4/nw8xx_jpgl.c:38:
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:50: warning: "struct RingQueue" declared inside parameter list
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:50: warning: its scope is only this definition or declaration, which is probably not what you want
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:57: warning: "struct RingQueue" declared inside parameter list
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `rqBR_init':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:65: warning: implicit declaration of function `RING_QUEUE_PEEK'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:69: warning: implicit declaration of function `RING_QUEUE_DEQUEUE_BYTES'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `jpgl_processFrame':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: warning: implicit declaration of function `printk'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: `KERN_NOTICE' undeclared (first use in this function)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: (Each undeclared identifier is reported only once
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: for each function it appears in.)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: parse error before string constant
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: warning: implicit declaration of function `kmalloc'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: error: `GFP_KERNEL' undeclared (first use in this function)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: warning: assignment makes pointer from integer without a cast
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:661: warning: implicit declaration of function `kfree'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `jpgl_findHeader':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:688: warning: implicit declaration of function `RingQueue_GetLength'
make[2]: *** [/home/dilnet/nw802-2.4/nw8xx_jpgl.o] Error 1
make[1]: *** [_module_/home/dilnet/nw802-2.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [default] Error 2
dilnet@dlntbldr:~/nw802-2.4$
```

Now I see there's an error so I guess it doesn't work.  Here's what the ls looks like before and after compilation:

ls before compile:
```
dilnet@dlntbldr:~/nw802-2.4$ ls
Changelog         Makefile              nw802.init       README
cvideopro.init    Makefile.26           nw8xx_jpgl.c     SpaceCam.init
d-link-350c.init  mustek_300_mini.init  nw8xx_jpgl.h     trust_space.init
DS3303u.init      nw800.init            nw8xx_regedit.c  Twinkle.init
kritter.init      nw801.init            patch-2.6        usbvideo.c
LICENSE           nw802.c               proscope.init    usbvideo.h
```

ls after compile:
```
dilnet@dlntbldr:~/nw802-2.4$ ls
Changelog         DS3303u.init  Makefile              nw800.init  nw802.c.orig  nw8xx_jpgl.h     proscope.init  trust_space.init  [COLOR="Red"]usbvideo.h[/COLOR]
cvideopro.init    kritter.init  Makefile.26           nw801.init  nw802.init    nw8xx_regedit.c  README         Twinkle.init
d-link-350c.init  LICENSE       mustek_300_mini.init  nw802.c     nw8xx_jpgl.c  patch-2.6        SpaceCam.init  [COLOR="Red"]usbvideo.c[/COLOR]
```

notice the changes of files usbvideo.c and usbvideo.h.  They become links to something else.  Links to where?

```
dilnet@dlntbldr:~/nw802-2.4$ readlink usbvideo.c
/lib/modules/2.6.12-10-386/build/drivers/usb/media/usbvideo.c
dilnet@dlntbldr:~/nw802-2.4$ readlink usbvideo.h
/lib/modules/2.6.12-10-386/build/drivers/usb/media/usbvideo.h
```

this is weird to me, since /lib/modules blabla does not exist.
```
dilnet@dlntbldr:~/nw802-2.4$ ls /lib/modules/2.6.12-10-386/build/drivers/usb/media/
Kconfig  Makefile  [COLOR="Blue"]pwc[/COLOR]  [COLOR="Blue"]quickcam[/COLOR]  [COLOR="Blue"]spca5xx[/COLOR]
dilnet@dlntbldr:~/nw802-2.4$
```

So I thought that it was some script screwup or something which was supposed to be done by root.

I tried to make it as root:
```
dilnet@dlntbldr:~/nw802-2.4$ su
Password:
root@dlntbldr:/home/dilnet/nw802-2.4# make clean
rm -f usbvideo.h usbvideo.c *.o *.ko *~ *.mod.c
root@dlntbldr:/home/dilnet/nw802-2.4# make
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.h .
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.c .
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/dilnet/nw802-2.4/nw8xx_jpgl.o
In file included from /home/dilnet/nw802-2.4/nw8xx_jpgl.c:38:
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:43:22: usbvideo.h: No such file or directory
In file included from /home/dilnet/nw802-2.4/nw8xx_jpgl.c:38:
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:50: warning: "struct RingQueue" declared inside parameter list
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:50: warning: its scope is only this definition or declaration, which is probably not what you want
/home/dilnet/nw802-2.4/nw8xx_jpgl.h:57: warning: "struct RingQueue" declared inside parameter list
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `rqBR_init':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:65: warning: implicit declaration of function `RING_QUEUE_PEEK'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:69: warning: implicit declaration of function `RING_QUEUE_DEQUEUE_BYTES'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `jpgl_processFrame':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: warning: implicit declaration of function `printk'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: `KERN_NOTICE' undeclared (first use in this function)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: (Each undeclared identifier is reported only once
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: for each function it appears in.)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:469: error: parse error before string constant
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: warning: implicit declaration of function `kmalloc'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: error: `GFP_KERNEL' undeclared (first use in this function)
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:479: warning: assignment makes pointer from integer without a cast
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:661: warning: implicit declaration of function `kfree'
/home/dilnet/nw802-2.4/nw8xx_jpgl.c: In function `jpgl_findHeader':
/home/dilnet/nw802-2.4/nw8xx_jpgl.c:688: warning: implicit declaration of function `RingQueue_GetLength'
make[2]: *** [/home/dilnet/nw802-2.4/nw8xx_jpgl.o] Error 1
make[1]: *** [_module_/home/dilnet/nw802-2.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [default] Error 2
root@dlntbldr:/home/dilnet/nw802-2.4#
```

same error, so I don't think I can continue.

Any help on this?  I'm going to email the developers, but the last sourceforge update was around a year ago.

Other useful information?
here's my version of kernel
kernel 2.6.12-10-386

--oops I just realized I didn't have kernel source.  But I have kernel headers.  ach.  But aren't the kernel headers supposed to be enough for making modules?

am downloading kernel source right now.

---

### Post by ephman on 2005-12-28
same errors, but downloading the source didn't help.  did you ever get a fix for this???

thanks,
ephman

---

### Post by the_it on 2006-01-04
I was finally able to download kernel source and build the module manually.  It's been a while though, so I don't remember what I did anymore, but basically I built the module and got a nwblabla.ko output, put that in the modules directory, did a depmod then modprobe and got all modules to load in the kernel.

I plug in the device and I get to make a cam device appear, but nothing happens when I run xinerama or whatever cam application (black output).  It's not the camera or the usb port though, since both are proven to work.

---

### Post by canadiandude007 on 2007-11-20
I'm still having issues.  I'm using version 2.6.22-14-generic of Ubuntu

I tried installing the source, but is there a apt package I can download?

The Makefile is as follows:

KERNEL_SOURCE ?= /lib/modules/`uname -r`/build

obj-m := nw8xx.o usbvideo.o
nw8xx-objs := nw8xx_jpgl.o nw802.o


default: 
	ln -sf ${KERNEL_SOURCE}/drivers/media/video/usbvideo/usbvideo.h .
	ln -sf ${KERNEL_SOURCE}/drivers/media/video/usbvideo/usbvideo.c .
	make -C ${KERNEL_SOURCE} SUBDIRS=`pwd` modules

clean:
	rm -f usbvideo.h usbvideo.c *.o *.ko *~ *.mod.c



I tried to copy a version of the usbvideo.h and usbvideo.c files to those above folders.  However when I type in Make as root (sudo -s) I'm getting error messages such as:

usbvideo.h:26: error: expected identifier or ‘(’ before ‘%’ token


Any suggestions?

---

### Post by canadiandude007 on 2007-11-28
See this thread for further updates: [http://ubuntuforums.org/showthread.php?t=621240](http://ubuntuforums.org/showthread.php?t=621240)

---

