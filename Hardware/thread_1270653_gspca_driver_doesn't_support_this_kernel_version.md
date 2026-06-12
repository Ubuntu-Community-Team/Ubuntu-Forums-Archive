---
title: "gspca driver doesn't support this kernel version?"
date: 2009-09-19
forum: Hardware
---

### Post by Unparallelogram on 2009-09-19
I have a webcam/microphone that I'm trying to get drivers for. It shows up under lsusb as Bus 001 Device 002: ID 0ac8:3420 Z-Star Microelectronics Corp. As far as I can tell, the driver I need is called gspca. I can only seem to find the source for this, which is quite old and doesn't compile against the current kernel. This is also true of the source available in the repo. I have kernel-headers and build-essential installed. I can't tell if it's just incompatible now or if I'm doing something wrong. Please advise. Thanks.

I'm using the directions from [http://ubuntuforums.org/showthread.php?t=1269288&highlight=gspca](http://ubuntuforums.org/showthread.php?t=1269288&highlight=gspca)

My error message is
> mpan@unparallelogram:/usr/src/modules/gspca$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
Assembler messages:
Fatal error: can't create /usr/src/modules/gspca/.tmp_gspca_core.o: Permission denied
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/src/modules/gspca/gspca_core.c:859:
/usr/src/modules/gspca/Mars-Semi/mr97311.h: In function &#8216;mr97311_stopN&#8217;:
/usr/src/modules/gspca/Mars-Semi/mr97311.h:109: warning: pointer targets in passing argument 3 of &#8216;pcam_reg_write&#8217; differ in signedness
In file included from /usr/src/modules/gspca/gspca_core.c:861:
/usr/src/modules/gspca/Pixart/pac7311.h: In function &#8216;pac7311_reg_write&#8217;:
/usr/src/modules/gspca/Pixart/pac7311.h:79: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h: In function &#8216;pac7311_start&#8217;:
/usr/src/modules/gspca/Pixart/pac7311.h:218: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:219: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:220: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:221: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:222: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:223: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:224: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:225: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:226: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:227: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:228: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:229: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:230: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:231: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:232: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:233: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:234: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:235: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:236: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/Pixart/pac7311.h:237: warning: pointer targets in passing argument 5 of &#8216;spca5xxRegWrite&#8217; differ in signedness
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_alloc&#8217;:
/usr/src/modules/gspca/gspca_core.c:1735: warning: pointer targets in assignment differ in signedness
/usr/src/modules/gspca/gspca_core.c:1740: warning: pointer targets in assignment differ in signedness
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 2
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
mpan@unparallelogram:/usr/src/modules/gspca$ 


---

### Post by jesterthejedi on 2009-09-20
I had trouble with my Microsoft vx-1000 on the new kernel in Karmic. Here is how I got it to install. Maybe this will work for you. You will have to reinstall after each kernel update!

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type these commands no quotes:
"make distclean" 
"make clean" 
"make menuconfig" - choose the gspca/your driver, exclude others
"make"
then type "sudo make install"
reboot

Tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

Camorama, Kopete, and Skype require:
"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype(or alt)" in terminal or a config file, search the forums for details.

---

### Post by Yellow Pasque on 2009-09-20
> Fatal error: can't create /usr/src/modules/gspca/.tmp_gspca_core.o: **Permission denied**
...
```
**sudo** make
```
:)

---

### Post by Unparallelogram on 2009-09-20
Jester's directions worked. Thank you. =)
Although, I have video but not sound. I think I might have messed up a setting somewhere. Any ideas?

EDIT: I poked some settings and volume controls. Now the sound works but my soundcard is spitting out some horrible static into my headphones occasionally.

---

### Post by jesterthejedi on 2009-09-21
> **Temüjin said:**
> ...
```
**sudo** make
```
:)

extract the gspca archive in your home or user permissable directory.

---

### Post by jesterthejedi on 2009-09-21
> **Unparallelogram said:**
> Jester's directions worked. Thank you. =)
Although, I have video but not sound. I think I might have messed up a setting somewhere. Any ideas?

EDIT: I poked some settings and volume controls. Now the sound works but my soundcard is spitting out some horrible static into my headphones occasionally.

karmic has some sound issues. as for static, make sure you dont have the gain settings on or too high.

---

### Post by Glanthor Reviol on 2009-10-25
> **jesterthejedi said:**
> 
Camorama, Kopete, and Skype require:
"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype(or alt)"

I installed on Karmic, and after years it finally works! And it works with skype, without this LD_PRELOAD thingy. WOOOW.

But, not everything is okay. The picture is a bit in red hue... The same in Cheese. A thin red layer. It's usable though, but it's like I'm on Mars :) It's anything I can do?

---

### Post by frisket on 2010-06-07
> **jesterthejedi said:**
> I had trouble with my Microsoft vx-1000 on the new kernel in Karmic. Here is how I got it to install. Maybe this will work for you. You will have to reinstall after each kernel update!

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)

This directory has been deleted. Elsewhere on linuxtv.org I saw something about ~jfrancois/gspca having been "merged" with something, so maybe it has been permanently removed.

Does anyone have a copy of whatever package was referred to? The original post doesn't give the filename.

---

