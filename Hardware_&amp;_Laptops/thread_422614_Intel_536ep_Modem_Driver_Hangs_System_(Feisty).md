---
title: "Intel 536ep Modem Driver Hangs System (Feisty)"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by zekica on 2007-04-25
I have Intel 536EP modem, and i have istalled Ubuntu Feisty, and everything works fine except my modem.
I have standard ubuntu kernel installed:
```
filip@sun:~$ uname -r
2.6.20-15-generic
```
I have downloaded driver from [http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz) and it compiles and loads:
```
root@sun:~/intel-536EP-2.56.76.0# make 536
   Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.20-15-generic
make[1]: Entering directory `/root/intel-536EP-2.56.76.0/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/root/intel-536EP-2.56.76.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/coredrv.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/clmmain.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/rts.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/task.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/uart.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/wwh_dflt.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/locks.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/softserial_io.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/softserial_ioctl.o
  CC [M]  /root/intel-536EP-2.56.76.0/coredrv/softserial.o
/root/intel-536EP-2.56.76.0/coredrv/softserial.c: In function ‘softserial_background_event_handler’:
/root/intel-536EP-2.56.76.0/coredrv/softserial.c:331: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /root/intel-536EP-2.56.76.0/coredrv/Intel536.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/intel-536EP-2.56.76.0/coredrv/.536core.lib.cmd for /root/intel-536EP-2.56.76.0/coredrv/536core.lib
  CC      /root/intel-536EP-2.56.76.0/coredrv/Intel536.mod.o
  LD [M]  /root/intel-536EP-2.56.76.0/coredrv/Intel536.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/root/intel-536EP-2.56.76.0/coredrv'
```
modprobe loads this module without any problem.

But if I try to open the device (/dev/536ep0) for example with KPPP, the system hangs completely. 
I've read (on this forum) that this driver worked in 2.6.20-13 (in feisty beta).

---

### Post by DarkW0lf on 2007-05-06
Follow the dialup modem howto for the Intel 536 modem. It has worked for me for two versions now.

In kppp make sure that the 'stupid' mode is on. Or whatever it is called, I remember having problems in gnomeppp with that off.

Honestly I haven't tried it in feisty yet, I just aksed in the edgy howto posted in these forums whether a recompile is needed for feisty or the existing module works.

[http://ubuntuforums.org/showthread.php?t=302969&page=4](http://ubuntuforums.org/showthread.php?t=302969&page=4)

I'll post what I hear there if you don't find out anything first.

---

### Post by zekica on 2007-05-07
No, that is not my problem, I have a problem that my system hangs when any program tries to open /dev/modem.

I will try to compile this driver on live CD, and see if that works. If it works, I guess I will have to find what software/module is causing problems, this came to my mind because i have read that this driver worked for other people on the same kernel version.

Thanks, but as I said this is not the problem I have.

---

### Post by zekica on 2007-05-07
I've figured out what was the problem. The problem was that I have changed order of my PCI cards recently, and that coincided with Feisty install. The slot modem was in had some dust on.

It was a hardware problem, but thanks again for help.

---

### Post by DarkW0lf on 2007-05-20
Good it worked for you but some people have problems with Intel536 in feisty.

In any case I have found some updated modem packages in the linmodem site.
I wonder if they updated the Dialup howto at Ubuntu Wiki yet ?

Yep they have and the same package I found too, guess I have to want two onths after a release and chack the HowTo then. :-P

Forum HOWTO for Intel536
[http://ubuntuforums.org/showthread.php?t=302969&page=5](http://ubuntuforums.org/showthread.php?t=302969&page=5)

---

