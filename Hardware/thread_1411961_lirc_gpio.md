---
title: "lirc_gpio"
date: 2010-02-20
forum: Hardware
---

### Post by sherbert on 2010-02-20
I'm trying to follow this [guide]("http://www2.truman.edu/%7Edat725/htpc_single.html") in order to get my remote working with lirc. I got to these instructions:

> Then select "Save configuration & run configure". After configure is done, build your drivers:      sudo make
    


when I encountered some errors. This is what I get in the terminal when I key sudo make:

```
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.6'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.6/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
Making all in lirc_gpio
make[3]: Entering directory `/usr/src/lirc-0.8.6/drivers/lirc_gpio'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
make all
make[4]: Entering directory `/usr/src/lirc-0.8.6/drivers/lirc_gpio'
cp ./../lirc_dev/Module*.symvers .
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
    make -C /lib/modules/2.6.31-19-generic/build/ SUBDIRS=/usr/src/lirc-0.8.6/drivers/lirc_gpio modules \
        KBUILD_VERBOSE=1
make[5]: Entering directory `/usr/src/linux-source-2.6.31'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /usr/src/lirc-0.8.6/drivers/lirc_gpio/.tmp_versions ; rm -f /usr/src/lirc-0.8.6/drivers/lirc_gpio/.tmp_versions/*

  WARNING: Symbol version dump /usr/src/linux-source-2.6.31/Module.symvers
           is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.6/drivers/lirc_gpio
  gcc -Wp,-MD,/usr/src/lirc-0.8.6/drivers/lirc_gpio/.lirc_gpio.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-source-2.6.31/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.6/drivers/lirc_gpio/. -I/usr/src/lirc-0.8.6/drivers/lirc_gpio/ -I/usr/src/lirc-0.8.6/drivers/lirc_gpio/../.. -I/usr/src/lirc-0.8.6/drivers/lirc_gpio/../.. -I/lib/modules/2.6.31-19-generic/build//include/ -I/lib/modules/2.6.31-19-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_gpio)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_gpio)"  -c -o /usr/src/lirc-0.8.6/drivers/lirc_gpio/.tmp_lirc_gpio.o /usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
In file included from /usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c:56:
include/../drivers/media/video/bt8xx/bttvp.h:285:1: warning: this is the location of the previous definition
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c: In function ‘get_queue’:
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c:404: error: implicit declaration of function ‘bttv_get_gpio_queue’
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c:404: warning: return makes pointer from integer without a cast
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c: In function ‘init_module’:
/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.c:515: error: implicit declaration of function ‘bttv_get_cardinfo’
make[6]: *** [/usr/src/lirc-0.8.6/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[5]: *** [_module_/usr/src/lirc-0.8.6/drivers/lirc_gpio] Error 2
make[5]: Leaving directory `/usr/src/linux-source-2.6.31'
make[4]: *** [lirc_gpio.o] Error 2
make[4]: Leaving directory `/usr/src/lirc-0.8.6/drivers/lirc_gpio'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.6/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.6/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.6'
make: *** [all] Error 2

```

I've searched everywhere and can't find a solution for this. Best I could find is a workaround in which the /lirc/hardware.conf file is edited, which I have tried but the remote doesn't work at all with that.

Anyone got an idea?

---

### Post by sandu.lulu on 2010-03-11
i have the same issue.. i think it's been 2 weeks since i installed ubuntu and each day i had to search for a fix for some other issue..

---

