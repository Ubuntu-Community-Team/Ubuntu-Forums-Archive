---
title: "Cant make coretemp.c"
date: 2008-07-10
forum: Hardware
---

### Post by rabusmar on 2008-07-10
Hello. Im trying to make lm-sensors run under mi laptop. I have a compal JFL92 with an core 2 duo Peryn T9300 with ubuntu hardy x64.
I downloaded the latest sensors-detect (because the one that ships with the package is a little outdated) and tells me to insert module coretemp for sensors to get the temperature of my processor. However, trying that results in the following:
```

FATAL: Error inserting coretemp (/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/coretemp.ko): No such device

```
After googling for a while, i found that the coretemp of hardy linux kernel is outdated, as seen here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235119). However, in the same page some people claims that the coretemp of the kernel version 2.6.25 works fine, so im trying to insert that module into my kernel version 2.6.24-19-generic.
I have linux-headers-xxx and also build-essential. I downloaded the source code of linux kernel 2.6.25 and grabbed the coretemp.c file (which is also the same that appears on interpid kernel 2.6.26). I made a Makefile with the following content:
```

obj-m += coretemp.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
But issuing a make outputs the following errors:
```

rabusmar@beast:~/Downloads/coretemp$ make
make -C /lib/modules/2.6.24-19-generic/build M=/home/rabusmar/Downloads/coretemp modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/rabusmar/Downloads/coretemp/coretemp.o
/home/rabusmar/Downloads/coretemp/coretemp.c:395: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__refdata’
/home/rabusmar/Downloads/coretemp/coretemp.c: In function ‘coretemp_init’:
/home/rabusmar/Downloads/coretemp/coretemp.c:439: error: ‘coretemp_cpu_notifier’ undeclared (first use in this function)
/home/rabusmar/Downloads/coretemp/coretemp.c:439: error: (Each undeclared identifier is reported only once
/home/rabusmar/Downloads/coretemp/coretemp.c:439: error: for each function it appears in.)
/home/rabusmar/Downloads/coretemp/coretemp.c: In function ‘coretemp_exit’:
/home/rabusmar/Downloads/coretemp/coretemp.c:461: error: ‘coretemp_cpu_notifier’ undeclared (first use in this function)
make[2]: *** [/home/rabusmar/Downloads/coretemp/coretemp.o] Error 1
make[1]: *** [_module_/home/rabusmar/Downloads/coretemp] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

```
So im wondering if im missing something. Im not quite experienced in linux, so any suggestion is appreciated, because im a little obsessive and this problem doesnt let my concentrate at work xD!
Thanks in advance

---

### Post by phidia on 2008-07-10
I almost think you need to ask this in the programming section, but maybe someone here can say what those make errors are.
I am using gutsy 64 bit on an HP pavilion laptop and lm-sensors works fine-installed with apt. I wonder what, in a practical way, the most recent release provides over the repo package?

---

