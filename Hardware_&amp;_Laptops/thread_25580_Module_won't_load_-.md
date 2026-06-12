---
title: "Module won't load -"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by rch on 2005-04-10
I've been trying to compile the zc030x (various webcams) module, and after some fiddling around I managed to compile it, however, I can't insert it now. Insmod says this:

insmod: error inserting './zc030x.ko': -1 Invalid module format

And dmesg reports:


zc030x: no version for "struct_module" found: kernel tainted.
zc030x: version magic '2.6.8-1 SMP preempt PENTIUM4 gcc-3.3' should be '2.6.8.1-5-686 preempt 686 gcc-3.3'



I've been trying to find a cure, but so far in vain. Does anyone know in which file the "PENTIUM4" might be in the kernel sources, so I might change it to 686 as it should be, or another way to fix this? insmod needs and -f  :-|

---

### Post by rch on 2005-04-10
...And now, while fiddling around, I got to a point where I need to recompile the module, but by now I've, of course, messesd things up so much that's impossible. I know I ran into these same errors before, but I can't for the life of me, remember what I did to 'em. I seem to remember something about a "kernel-headers-xxx" package being the godsent saviour, but now I can't find anything like that, and the kernel-source-xxx packages should include the same things and mor, right? Well, anyway, here's the output from make, if anyone can figure out what I might've done last time to make it work, please help :/

```
root@lime:~/zc030x # make
   Building ZC030X driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pln/zc030x modules
make[1]: Entering directory `/usr/src/kernel-source-2.6.8'
Makefile:418: .config: No such file or directory
  CC [M]  /home/pln/zc030x/zc030x_main.o
In file included from /home/pln/zc030x/zc030x_main.c:14:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
/home/pln/zc030x/zc030x_main.c:15:27: linux/version.h: No such file or directory
/home/pln/zc030x/zc030x_main.c:18:40: missing binary operator before token "("
In file included from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/asm/processor.h:67: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a functi on)
include/asm/processor.h:67: error: requested alignment is not a constant
In file included from include/linux/list.h:7,
                 from include/linux/wait.h:14,
                 from include/asm/semaphore.h:41,
                 from include/linux/sched.h:18,
                 from include/linux/module.h:10,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/linux/prefetch.h: In function `prefetch_range':
include/linux/prefetch.h:64: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared (first use in this f unction)
include/linux/prefetch.h:64: error: (Each undeclared identifier is reported only once
include/linux/prefetch.h:64: error: for each function it appears in.)
In file included from include/linux/module.h:23,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/asm/module.h:54:2: #error unknown processor family
In file included from include/asm/hardirq.h:6,
                 from include/linux/interrupt.h:12,
                 from include/linux/usb.h:15,
                 from /home/pln/zc030x/zc030x_main.c:32:
include/linux/irq.h: At top level:
include/linux/irq.h:68: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
include/linux/irq.h:68: error: requested alignment is not a constant
In file included from include/linux/interrupt.h:12,
                 from include/linux/usb.h:15,
                 from /home/pln/zc030x/zc030x_main.c:32:
include/asm/hardirq.h:13: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function )
include/asm/hardirq.h:13: error: requested alignment is not a constant
In file included from /home/pln/zc030x/zc030x_kerneldef.h:24,
                 from /home/pln/zc030x/zc030x_main.c:37:
include/linux/videodev.h:5:27: linux/version.h: No such file or directory
In file included from /home/pln/zc030x/zc030x_main.c:37:
/home/pln/zc030x/zc030x_kerneldef.h:41:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:66:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:73:30: linux/tqueue.h: No such file or directory
/home/pln/zc030x/zc030x_kerneldef.h:77:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:224:44: missing binary operator before token "("
In file included from /home/pln/zc030x/zc030x_main.c:41:
/home/pln/zc030x/zc030x_v4l.h:12:40: missing binary operator before token "("
In file included from /home/pln/zc030x/zc030x_main.c:53:
/home/pln/zc030x/zc030x_isochron.h:30:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:95:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:142:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:148: error: conflicting types for `zc030x_probe'
/home/pln/zc030x/zc030x_main.c:99: error: previous declaration of `zc030x_probe'
/home/pln/zc030x/zc030x_main.c:155:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: In function `zc030x_probe':
/home/pln/zc030x/zc030x_main.c:159: warning: declaration of `udev' shadows a parameter
/home/pln/zc030x/zc030x_main.c:159: error: `intf' undeclared (first use in this function)
/home/pln/zc030x/zc030x_main.c:175:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:185:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:213:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:221:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:223:42: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:281:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:291:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:294: warning: return makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:303:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:307: warning: return makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:314:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: At top level:
/home/pln/zc030x/zc030x_main.c:321: error: conflicting types for `zc030x_disconnect'
/home/pln/zc030x/zc030x_main.c:100: error: previous declaration of `zc030x_disconnect'
/home/pln/zc030x/zc030x_main.c:325:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:368:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:399:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:489:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:505:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:710:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:715:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: In function `zc030x_mmap':
/home/pln/zc030x/zc030x_main.c:718: warning: passing arg 1 of `remap_page_range' makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:718: error: incompatible type for argument 4 of `remap_page_rang e'
/home/pln/zc030x/zc030x_main.c:718: error: too few arguments to function `remap_page_range'
make[2]: *** [/home/pln/zc030x/zc030x_main.o] Error 1
make[1]: *** [_module_/home/pln/zc030x] Error 2
make[1]: Leaving directory `/usr/src/kernel-source-2.6.8'
make: *** [default] Error 2


```

---

### Post by az on 2005-04-10
Foret about the kernel-source, it is unconfigured.  Just install the linux-headers package that matches your running kernel

uname -r
apt-cache search linux-headers.


messed up the linux-source?  Delete the directory and untar it again.  But you won't need to do that if you use the linux-headers.

kernel-headers is a debian package.  Linux-headers is Ubuntu.

---

### Post by rabantu on 2007-12-26
> **rch said:**
> ...And now, while fiddling around, I got to a point where I need to recompile the module, but by now I've, of course, messesd things up so much that's impossible. I know I ran into these same errors before, but I can't for the life of me, remember what I did to 'em. I seem to remember something about a "kernel-headers-xxx" package being the godsent saviour, but now I can't find anything like that, and the kernel-source-xxx packages should include the same things and mor, right? Well, anyway, here's the output from make, if anyone can figure out what I might've done last time to make it work, please help :/

```
root@lime:~/zc030x # make
   Building ZC030X driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pln/zc030x modules
make[1]: Entering directory `/usr/src/kernel-source-2.6.8'
Makefile:418: .config: No such file or directory
  CC [M]  /home/pln/zc030x/zc030x_main.o
In file included from /home/pln/zc030x/zc030x_main.c:14:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
/home/pln/zc030x/zc030x_main.c:15:27: linux/version.h: No such file or directory
/home/pln/zc030x/zc030x_main.c:18:40: missing binary operator before token "("
In file included from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/asm/processor.h:67: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a functi on)
include/asm/processor.h:67: error: requested alignment is not a constant
In file included from include/linux/list.h:7,
                 from include/linux/wait.h:14,
                 from include/asm/semaphore.h:41,
                 from include/linux/sched.h:18,
                 from include/linux/module.h:10,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/linux/prefetch.h: In function `prefetch_range':
include/linux/prefetch.h:64: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared (first use in this f unction)
include/linux/prefetch.h:64: error: (Each undeclared identifier is reported only once
include/linux/prefetch.h:64: error: for each function it appears in.)
In file included from include/linux/module.h:23,
                 from /home/pln/zc030x/zc030x_main.c:28:
include/asm/module.h:54:2: #error unknown processor family
In file included from include/asm/hardirq.h:6,
                 from include/linux/interrupt.h:12,
                 from include/linux/usb.h:15,
                 from /home/pln/zc030x/zc030x_main.c:32:
include/linux/irq.h: At top level:
include/linux/irq.h:68: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
include/linux/irq.h:68: error: requested alignment is not a constant
In file included from include/linux/interrupt.h:12,
                 from include/linux/usb.h:15,
                 from /home/pln/zc030x/zc030x_main.c:32:
include/asm/hardirq.h:13: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function )
include/asm/hardirq.h:13: error: requested alignment is not a constant
In file included from /home/pln/zc030x/zc030x_kerneldef.h:24,
                 from /home/pln/zc030x/zc030x_main.c:37:
include/linux/videodev.h:5:27: linux/version.h: No such file or directory
In file included from /home/pln/zc030x/zc030x_main.c:37:
/home/pln/zc030x/zc030x_kerneldef.h:41:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:66:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:73:30: linux/tqueue.h: No such file or directory
/home/pln/zc030x/zc030x_kerneldef.h:77:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_kerneldef.h:224:44: missing binary operator before token "("
In file included from /home/pln/zc030x/zc030x_main.c:41:
/home/pln/zc030x/zc030x_v4l.h:12:40: missing binary operator before token "("
In file included from /home/pln/zc030x/zc030x_main.c:53:
/home/pln/zc030x/zc030x_isochron.h:30:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:95:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:142:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:148: error: conflicting types for `zc030x_probe'
/home/pln/zc030x/zc030x_main.c:99: error: previous declaration of `zc030x_probe'
/home/pln/zc030x/zc030x_main.c:155:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: In function `zc030x_probe':
/home/pln/zc030x/zc030x_main.c:159: warning: declaration of `udev' shadows a parameter
/home/pln/zc030x/zc030x_main.c:159: error: `intf' undeclared (first use in this function)
/home/pln/zc030x/zc030x_main.c:175:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:185:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:213:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:221:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:223:42: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:281:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:291:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:294: warning: return makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:303:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:307: warning: return makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:314:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: At top level:
/home/pln/zc030x/zc030x_main.c:321: error: conflicting types for `zc030x_disconnect'
/home/pln/zc030x/zc030x_main.c:100: error: previous declaration of `zc030x_disconnect'
/home/pln/zc030x/zc030x_main.c:325:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:368:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:399:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:489:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:505:40: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:710:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c:715:41: missing binary operator before token "("
/home/pln/zc030x/zc030x_main.c: In function `zc030x_mmap':
/home/pln/zc030x/zc030x_main.c:718: warning: passing arg 1 of `remap_page_range' makes pointer from integer without a cast
/home/pln/zc030x/zc030x_main.c:718: error: incompatible type for argument 4 of `remap_page_rang e'
/home/pln/zc030x/zc030x_main.c:718: error: too few arguments to function `remap_page_range'
make[2]: *** [/home/pln/zc030x/zc030x_main.o] Error 1
make[1]: *** [_module_/home/pln/zc030x] Error 2
make[1]: Leaving directory `/usr/src/kernel-source-2.6.8'
make: *** [default] Error 2


```



Hi rch,

I am running into this same issue. Can you please let me know how you fixed it? I am stuck on this for the last couple of days:confused:

---

