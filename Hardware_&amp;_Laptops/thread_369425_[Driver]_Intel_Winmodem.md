---
title: "[Driver] Intel Winmodem"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by Lepaca on 2007-02-24
I am a newbee in linux.
I installed Ubuntu 6.10 and I have to install a winmodem with Intel chipset

This is scanmodem output:
> [color=blue]PCIDEV=8086:1040
CLASS="Class 0780: 8086:1040"
NAME="Communication controller: Intel Corporation 536EP Data Fax Modem"
Vendor=8086
Device=1040
SUBSYS=5214:0034
SUBNAME=" Unknown device 5214:0034"
SUBven=5214
IRQ=5
Test="./scanModem test 8086:1040 5214:0034"
SLMODEMD_DEVICE=modem:1
PORT="modem:1"
Driver=snd-intel8x0m
DRIVER_=snd_intel8x0m
KDRIVER=SND_NTEL8X0M
MPLACE=[/color]

I downloaded from intel website, generic drivers for linux: [color=blue]Intel-536EP-4.71.tgz[/color]

I obtain an error. Here the console output:
> [color=blue]root@Hell:/home/ff/Intel-536# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/ff/Intel-536/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/ff/Intel-536/coredrv'
rm -f *.o *.ko

root@Hell:/home/ff/Intel-536# make 536
   Module precompile check
   Current running kernel is: 2.6.17-10-generic
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
2.6.17-10-generic
make[1]: Entering directory `/home/ff/Intel-536/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/ff/Intel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/ff/Intel-536/coredrv/coredrv.o
/home/ff/Intel-536/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/ff/Intel-536/coredrv/coredrv.c:73: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/ff/Intel-536/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/ff/Intel-536/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/ff/Intel-536/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/ff/Intel-536/coredrv/coredrv.c: In function ‘close’:
/home/ff/Intel-536/coredrv/coredrv.c:439: warning: implicit declaration of function ‘pm_unregister’
/home/ff/Intel-536/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/ff/Intel-536/coredrv/coredrv.c:587: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c:592: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c:593: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c:595: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c:596: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c:597: error: ‘struct tty_struct’ has no member named ‘flip’
/home/ff/Intel-536/coredrv/coredrv.c: At top level:
/home/ff/Intel-536/coredrv/coredrv.c:665: error: expected ‘)’ before string constant
/home/ff/Intel-536/coredrv/coredrv.c: In function ‘hamproc_write’:
/home/ff/Intel-536/coredrv/coredrv.c:684: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
/home/ff/Intel-536/coredrv/coredrv.c: At top level:
/home/ff/Intel-536/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/ff/Intel-536/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/ff/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/ff/Intel-536/coredrv'
2.6.17-10-generic
Failed to build driver
[/color]

I think that the problem is in this message: [color=blue]error: ‘struct tty_struct’ has no member named ‘flip’[/color]
but I don't know how to solve it...

thank you...

---

### Post by Lepaca on 2007-02-28
Please!!! Help me!!!!!
Free me, from windows!!!

---

