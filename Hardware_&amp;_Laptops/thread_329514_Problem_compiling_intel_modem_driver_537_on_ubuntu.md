---
title: "Problem compiling intel modem driver 537 on ubuntu 6 with kernel 2.6.17-10"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by kunalagon on 2007-01-01
I followed instuructions on page : [http://ubuntuforums.org/showthread.php?t=36762](http://ubuntuforums.org/showthread.php?t=36762) .

And I get theese errors:

```
euforia intel-537EP_secure-2.60.80.1 # make 537
   Module precompile check
   Current running kernel is: 2.6.18-kunalagon-Kunalagon
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.18-kunalagon-Kunalagon
make[1]: Entering directory `/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.18-kunalagon-Kunalagon/build SUBDIRS=/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-2.6.18-gentoo'
  CC [M]  /home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: type defaults to `int' in declaration of `EXPORT_SYMBOL_NOVERS'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `softcore_init_struct':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:336: warning: assignment from incompatible pointer type
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `open':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:394: warning: implicit declaration of function `pm_register'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:395: warning: assignment makes pointer from integer without a cast
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `close':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:416: warning: implicit declaration of function `pm_unregister'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `send_data_to_user':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:563: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:568: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:569: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:571: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:572: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:573: error: structure has no member named `flip'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: At top level:
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:641: error: parse error before string constant
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:641: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:641: warning: function declaration isn't a prototype
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:641: warning: data definition has no type or storage class
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `hamproc_write':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:660: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `kScheduleDPC':
/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:861: warning: implicit declaration of function `pm_access'
make[3]: *** [/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.18-gentoo'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/sorg/Desktop/intel537ep-2.80.60.1-drajveri+uputstvo/intel-537EP_secure-2.60.80.1/coredrv'
2.6.18-kunalagon-Kunalagon
Failed to build driver
euforia intel-537EP_secure-2.60.80.1 # 

```

Does somebody know what should I do to get driver be able to compile ?

---

### Post by FLPCGuy on 2007-01-02
I'm just guessing but there may have been a number transposition error (2.80.60 instead of 2.60.80) which caused a type mismatch and missing pieces in the build.

---

### Post by kunalagon on 2007-01-03
What that meas TRANSPOSITION ? There is only that driver for downloading. I dont understand you very vell, can you explane me more detailed ?

---

### Post by FLPCGuy on 2007-01-04
> **kunalagon said:**
> What that meas TRANSPOSITION ? There is only that driver for downloading. I dont understand you very vell, can you explane me more detailed ?

using 6 for 8 or 8 for 6.
/home/sorg/Desktop/intel537ep-2.**80.6**0.1-drajveri+uputstvo/intel-537EP_secure-2.**60.8**0.1/coredrv/coredrv.o

---

