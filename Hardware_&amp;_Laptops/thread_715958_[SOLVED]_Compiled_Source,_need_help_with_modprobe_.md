---
title: "[SOLVED] Compiled Source, need help with modprobe on CS330 webcam"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2008-03-05
I'm in the middle of trying to get my webcam up and running, using the guide located here:

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

I've gotten through downloading the correct source, extracting the tar, running make and make install all with no errors.  But when I get to the step that says to type "modprobe spca5xx"  It doesn't work.  Here's my terminal output from the whole ordeal so far:

```
root@zeke-desktop:~/Desktop# mv gspcav1-20071224.tar.gz /usr/src
root@zeke-desktop:~/Desktop# cd /usr/src
root@zeke-desktop:/usr/src# ls
gspcav1-20071224.tar.gz  linux-headers-2.6.22-14-386      spca5xx-v4l1goodbye
linux-headers-2.6.22-14  linux-headers-2.6.22-14-generic
root@zeke-desktop:/usr/src# tar xfvz gspcav1-20071224.tar.gz 
gspcav1-20071224/
gspcav1-20071224/decoder/
gspcav1-20071224/decoder/gspcadecoder.c
gspcav1-20071224/decoder/gspcadecoder.h
gspcav1-20071224/decoder/gspcadecoder-OSX.c
gspcav1-20071224/decoder/gspcadecoder-OSX.h
gspcav1-20071224/Makefile
gspcav1-20071224/Vimicro/
gspcav1-20071224/Vimicro/vc032x_sensor.h
gspcav1-20071224/Vimicro/zc3xx.h
gspcav1-20071224/Vimicro/cs2102.h
gspcav1-20071224/Vimicro/vc032x.h
gspcav1-20071224/Vimicro/pas106b.h
gspcav1-20071224/Vimicro/icm105a.h
gspcav1-20071224/Vimicro/hv7131b.h
gspcav1-20071224/Vimicro/hv7131c.h
gspcav1-20071224/Vimicro/pb0330.h
gspcav1-20071224/Vimicro/ov7630c.h
gspcav1-20071224/Vimicro/mc501cb.h
gspcav1-20071224/Vimicro/tas5130c_vf0250.h
gspcav1-20071224/Vimicro/ov7620.h
gspcav1-20071224/Vimicro/tas5130c.h
gspcav1-20071224/Vimicro/hdcs2020.h
gspcav1-20071224/Etoms/
gspcav1-20071224/Etoms/et61xx51.h
gspcav1-20071224/Sonix/
gspcav1-20071224/Sonix/sn9cxxx.h
gspcav1-20071224/Sonix/sonix.h
gspcav1-20071224/utils/
gspcav1-20071224/utils/spcagamma.h
gspcav1-20071224/utils/spcausb.h
gspcav1-20071224/utils/spcaCompat.h
gspcav1-20071224/Conexant/
gspcav1-20071224/Conexant/cx11646.h
gspcav1-20071224/Conexant/cxlib.h
gspcav1-20071224/Pixart/
gspcav1-20071224/Pixart/pac207-OSX.h
gspcav1-20071224/Pixart/pac7311.h
gspcav1-20071224/Pixart/pac207.h
gspcav1-20071224/changelog
gspcav1-20071224/license
gspcav1-20071224/gspca_core.c
gspcav1-20071224/Transvision/
gspcav1-20071224/Transvision/tv8532.h
gspcav1-20071224/Makefile.kld
gspcav1-20071224/gspca.h
gspcav1-20071224/Sunplus/
gspcav1-20071224/Sunplus/spca501.dat
gspcav1-20071224/Sunplus/spca505.dat
gspcav1-20071224/Sunplus/spca508.dat
gspcav1-20071224/Sunplus/spca561-OSX.h
gspcav1-20071224/Sunplus/spca506.h
gspcav1-20071224/Sunplus/spca561.h
gspcav1-20071224/Sunplus/spca501_init.h
gspcav1-20071224/Sunplus/spca508_init-OSX.h
gspcav1-20071224/Sunplus/spca508_init.h
gspcav1-20071224/Sunplus/spca501_init-OSX.h
gspcav1-20071224/Sunplus/spca505_init.h
gspcav1-20071224/Sunplus-jpeg/
gspcav1-20071224/Sunplus-jpeg/spca500.dat
gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20071224/Sunplus-jpeg/spca500_init.h
gspcav1-20071224/gspca_build
gspcav1-20071224/READ_AND_INSTALL
gspcav1-20071224/Mars-Semi/
gspcav1-20071224/Mars-Semi/mr97311.h
gspcav1-20071224/cutlog.py
root@zeke-desktop:/usr/src# ls
gspcav1-20071224         linux-headers-2.6.22-14-386
gspcav1-20071224.tar.gz  linux-headers-2.6.22-14-generic
linux-headers-2.6.22-14  spca5xx-v4l1goodbye
root@zeke-desktop:/usr/src# cd gspcav1-20071224/
root@zeke-desktop:/usr/src/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20071224 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-386'
  CC [M]  /usr/src/gspcav1-20071224/gspca_core.o
  CC [M]  /usr/src/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /usr/src/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/gspcav1-20071224/gspca.mod.o
  LD [M]  /usr/src/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'
root@zeke-desktop:/usr/src/gspcav1-20071224# modeprobe -r spca5xx
bash: modeprobe: command not found
root@zeke-desktop:/usr/src/gspcav1-20071224# modprobe -r spca5xx
FATAL: Module spca5xx not found.
root@zeke-desktop:/usr/src/gspcav1-20071224# make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
root@zeke-desktop:/usr/src/gspcav1-20071224# modprobe spca5xx
FATAL: Module spca5xx not found.
root@zeke-desktop:/usr/src/gspcav1-20071224# modprobe gspcav1
FATAL: Module gspcav1 not found.
root@zeke-desktop:/usr/src/gspcav1-20071224# 


```

You'll notice at the very end I tried to modify the name of the module to see if it would work, but it didn't.

Anyway, I know I'm close to getting this thing working.  Can someone please help me?

---

### Post by diablo75 on 2008-03-05
Looks like I got it working after all, but I noticed one command that I overlooked:

```
ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build 
```

I then ran make and then make install after that.

The Modprobe command still didnt't want to work with anything I fed it, but after restarting the computer, and checking with dmesg, I got this output:

```
zeke@zeke-desktop:~$ dmesg |grep camer
[   47.376884] /usr/src/gspcav1-20071224/gspca_core.c: USB GSPCA camera found. (SPCA501 )
zeke@zeke-desktop:~$ 

```

And I just checked it in Skype and it works!

Anybody know how to adjust video quality?  :)

---

