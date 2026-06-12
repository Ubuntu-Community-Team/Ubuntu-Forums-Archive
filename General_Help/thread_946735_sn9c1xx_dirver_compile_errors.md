---
title: "sn9c1xx dirver compile errors"
date: 2008-10-13
forum: General Help
---

### Post by randomas on 2008-10-13
Hallo I'm trying to compile the free sn9c1xx ([here]("http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2") )driver for my hercules classic silver that gives an lsusb response of 
```
Bus 001 Device 005: ID 06f8:3004 Guillemot Corp. 
```
That turns out to have a sn9c105 chip from casual googling.

This is the compile error I get:
```
**************************************************************************
* Building Video4Linux2 driver v1.48 for SN9C1xx PC Camera Controllers...*
* Official Linux 2.6.19 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/matteo/Downloads/sn9c1xx-1.48 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.o
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_reg’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1041: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_reg’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1066: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_val’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1099: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_val’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1132: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_i2c_reg’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1169: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_i2c_reg’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1196: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_i2c_val’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1229: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_i2c_val’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1267: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_store_green’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1313: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_show_frame_header’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1391: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_create_sysfs’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:1422: warning: initialization from incompatible pointer type
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c: In function ‘sn9c102_usb_probe’:
/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.c:3302: error: ‘struct video_device’ has no member named ‘hardware’
make[2]: *** [/home/matteo/Downloads/sn9c1xx-1.48/sn9c102_core.o] Error 1
make[1]: *** [_module_/home/matteo/Downloads/sn9c1xx-1.48] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [modules] Error 2

``` 

I'm on a stock kernel for ubuntu hardy x86-64 (I also tried on an x86 machine, same error). 

Any help is appreciated.

I also tried the microdia free driver in development, but that don't work either. 

TIA

Matt

---

### Post by tqft on 2008-10-13
1) I know your pain - at least similar
2) don't give up just yet
3) my guess is that it looks like the driver isn't seeing the kernel headers it needs to see when it is compiling/linking - so are the kernel headers for the kernel you are running installed?  I can see the ref's to the linux-header directory below but I have made that mistake before.

[http://ubuntuforums.org/archive/index.php/t-8554.html](http://ubuntuforums.org/archive/index.php/t-8554.html)

sudo apt-get install linux-headers-`uname -r`



Take all of the above with a grain of salt - I have had a webcam for 2 years and only had it working internittently - worked sort of until I installed TV card which screwed something up.  My next attempt at a solution - am going to try the 2.6.27 kernel with all sorts of webcam godoness built in - the gspca stuff has basically been mainlined into the kernel, along with uvc.  I don't pretend to understand - just hopefully going to work for me.

---

### Post by randomas on 2008-10-14
Unfortunately the headers are the right ones (they work fine for compileing the ov51x and microdia modlues). 

From the heights of my ignorance it looks like the driver is not compatable with this kernel version ... 

I think I'm better off returning the cam, pity though, it's nice for being as cheap as it is ...

---

