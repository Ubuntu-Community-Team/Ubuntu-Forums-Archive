---
title: "[Comedi] Failed to compile comedi on 9.04"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by Fredvs79 on 2009-08-06
I downloaded the 2.6.29.4 kernel source from kernel.org, and extracted it to /usr/src/. I downloaded RTAI 0.7.1 and patched the kernel, configured it, compiled it, installed it, rebooted and ran it.

Now I am trying to install comedi and comedilib. I got the tarballs off the web from comedi.org.

comedi-0.7.76 was extracted to /usr/local/bin
comedilib-0.8.1 was extracted to /usr/local/lib

I went back into my /usr/src/linux directory and edited the makefile to reflect my extraversion.
```

$ ls -l /usr/src
lrwxrwxrwx  1 root src         31 2009-08-05 13:53 linux -> linux-build-2.6.29.4-rtai-3.7.1
drwxrwxr-x 23 root root      4096 2009-08-06 00:41 linux-build-2.6.29.4-rtai-3.7.1
drwxr-xr-x 21 root root      4096 2009-08-05 15:08 linux-headers-2.6.29.4-rtai-3.7.1
$ uname -r 
2.6.29.4-rtai-3.7.1
$ sudo vi /usr/src/linux/Makefile

EXTRAVERSION = .4-rtai-3.7.1
```

I then cleaned up the area and prepared it for comedi

```
$ cd /usr/src/linux
$ sudo -s 
# make clean
# make mrproper
# make oldconfig
# make modules_prepare
# exit
```

Then I tried to compile comedi
```

$ ls -l /usr/local/bin
lrwxrwxrwx 1 root root    28 2009-08-05 15:27 comedi -> /usr/local/bin/comedi-0.7.76
drwxr-xr-x 8 daq  daq   4096 2009-08-06 01:00 comedi-0.7.76
$ cd /usr/local/bin/comedi
$ sudo -s
# ./configure

```

At this point I expected to be asked questions about configuring comedi for national instruments boards, however, the script ran without any intervention on my part. :confused:

```
# make
```

and here is the output

```
make  all-recursive
make[1]: Entering directory `/usr/local/bin/comedi-0.7.76'
Making all in comedi
make[2]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi'
Making all in .
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi'
if test "." != "."; then \
		for dir in . drivers kcomedilib drivers/addi-data; do \
			for file in `ls /usr/local/bin/comedi-0.7.76/comedi/$dir/*\.[ch] /usr/local/bin/comedi-0.7.76/comedi/$dir/Kbuild | /bin/grep -E -v \.mod\.c`; do \
				LINK_NAME=$dir/`basename "$file"`; \
				if test ! -e $LINK_NAME; then ln -vs $file $LINK_NAME; fi; \
			done; \
		done; \
	fi
make -I/usr/local/bin/comedi-0.7.76/comedi -C /lib/modules/2.6.29.4-rtai-3.7.1/build M=/usr/local/bin/comedi-0.7.76/comedi CC="gcc -I/usr/local/bin/comedi-0.7.76/ \
		-I/usr/local/bin/comedi-0.7.76/include -I/usr/realtime/include " modules
make[4]: Entering directory `/usr/src/linux-build-2.6.29.4-rtai-3.7.1'

  [COLOR="Red"]WARNING[/COLOR]: Symbol version dump /usr/src/linux-build-2.6.29.4-rtai-3.7.1/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/local/bin/comedi-0.7.76/comedi/comedi_fops.o
In file included from /usr/local/bin/comedi-0.7.76/include/linux/mutex.h:41,
                 from include/linux/notifier.h:13,
                 from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:644,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/local/bin/comedi-0.7.76/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:298,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_compat32.h:31,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:28:
/usr/local/bin/comedi-0.7.76/include/asm/semaphore.h:18:32: [COLOR="Red"]error:[/COLOR] asm/semaphore.h: No such file or directory
In file included from include/linux/notifier.h:15,
                 from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:644,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/local/bin/comedi-0.7.76/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:298,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_compat32.h:31,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:28:
include/linux/srcu.h:37: [COLOR="Red"]error:[/COLOR] field ‘semaphore’ has incomplete type
In file included from include/linux/memory_hotplug.h:6,
                 from include/linux/mmzone.h:644,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/local/bin/comedi-0.7.76/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:298,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_compat32.h:31,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:28:
include/linux/notifier.h:71: [COLOR="Red"]error:[/COLOR] field ‘semaphore’ has incomplete type
In file included from /usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/acpi.h:30,
                 from /usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/fixmap_32.h:28,
                 from /usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:767,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /usr/local/bin/comedi-0.7.76/include/linux/slab.h:8,
                 from include/linux/percpu.h:5,
                 from include/linux/rcupdate.h:39,
                 from include/linux/rculist.h:10,
                 from include/linux/dcache.h:6,
                 from include/linux/fs.h:298,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_compat32.h:31,
                 from /usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:28:
/usr/src/linux-build-2.6.29.4-rtai-3.7.1/arch/x86/include/asm/mmu.h:14: [COLOR="Red"]error:[/COLOR] field ‘lock’ has incomplete type
/usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c: In function ‘comedi_init’:
/usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:1918: [COLOR="Red"]error:[/COLOR] implicit declaration of function ‘class_device_create’
/usr/local/bin/comedi-0.7.76/comedi/comedi_fops.c:1918: [COLOR="Red"]warning[/COLOR]: assignment makes pointer from integer without a cast
make[5]: *** [/usr/local/bin/comedi-0.7.76/comedi/comedi_fops.o] [COLOR="Red"]Error 1[/COLOR]
make[4]: *** [_module_/usr/local/bin/comedi-0.7.76/comedi] [COLOR="Red"]Error 2[/COLOR]
make[4]: Leaving directory `/usr/src/linux-build-2.6.29.4-rtai-3.7.1'
make[3]: [all-local] [COLOR="Red"]Error 2[/COLOR] (ignored)
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi'
Making all in kcomedilib
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi/kcomedilib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi/kcomedilib'
Making all in drivers
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi/drivers'
Making all in addi-data
make[4]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi/drivers/addi-data'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi/drivers/addi-data'
make[4]: Entering directory `/usr/local/bin/comedi-0.7.76/comedi/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi/drivers'
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi/drivers'
make[2]: Leaving directory `/usr/local/bin/comedi-0.7.76/comedi'
Making all in include
make[2]: Entering directory `/usr/local/bin/comedi-0.7.76/include'
Making all in asm
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/include/asm'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/include/asm'
Making all in linux
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/include/linux'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/include/linux'
Making all in pcmcia
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/include/pcmcia'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/include/pcmcia'
make[3]: Entering directory `/usr/local/bin/comedi-0.7.76/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/local/bin/comedi-0.7.76/include'
make[2]: Leaving directory `/usr/local/bin/comedi-0.7.76/include'
make[2]: Entering directory `/usr/local/bin/comedi-0.7.76'
make[2]: Leaving directory `/usr/local/bin/comedi-0.7.76'
make[1]: Leaving directory `/usr/local/bin/comedi-0.7.76'

```

I then checked to see if the comedi kernel module was compiled 
```

$ ls /usr/local/bin/comedi/comedi/drivers/comedi.ko
ls: cannot access /usr/local/bin/comedi/comedi/drivers/comedi.ko: No such file or directory
$ ls /usr/local/bin/comedi/comedi/drivers/*.ko
ls: cannot access /usr/local/bin/comedi/comedi/drivers/*.ko: No such file or directory
```

At this point I dont see why it fails, but I believe this is the reason why I haven't been able to proceed to loading the ni_pcimio module. Most of the help I've found on the web has not helped. Getting comedi to compile is difficult because it depends on the kernel headers. I thought I had all that sorted, but I'm thinking I'm missing something. 

Any help would be appreciated.

---

