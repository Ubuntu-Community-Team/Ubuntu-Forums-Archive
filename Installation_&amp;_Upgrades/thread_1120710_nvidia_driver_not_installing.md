---
title: "nvidia driver not installing"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-04-09
hey all

I just installed the 2.6.30-020630rc1-generic through ubuntus kernel team ppa but it and my nvidia driver dosent seem to like eachother, nvidia driver fails with bad exit status 10. 


the /var/lib/dkms/nvidia/180.44/build/make.log  is shown below:

```
DKMS make.log for nvidia-180.44 for kernel 2.6.30-020630rc1-generic (i686)
Thu Apr  9 15:14:05 CEST 2009
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.30-020630rc1-generic/build SUBDIRS=/var/lib/dkms/nvidia/180.44/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia/180.44/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/180.44/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/180.44/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/180.44/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -Iinclude  -I/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include -include include/linux/autoconf.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/var/lib/dkms/nvidia/180.44/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"180.44\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/180.44/build/.tmp_nv.o /var/lib/dkms/nvidia/180.44/build/nv.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function &#8216;set_bit&#8217;:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:64: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function &#8216;clear_bit&#8217;:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:102: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h: In function &#8216;change_bit&#8217;:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/bitops.h:178: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:19,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
include/linux/sched.h:2119: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/io.h:22,
                 from include/linux/pci.h:54,
                 from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/io.h: In function &#8216;writeq&#8217;:
/usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/io.h:70: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.30-020630rc1-generic/arch/x86/include/asm/pci.h:129,
                 from include/linux/pci.h:1098,
                 from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:86,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used in arithmetic
In file included from /var/lib/dkms/nvidia/180.44/build/nv-linux.h:113,
                 from /var/lib/dkms/nvidia/180.44/build/nv.c:14:
include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
include/linux/highmem.h:147: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:147: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:147: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:147: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:150: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:150: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:150: warning: pointer of type &#8216;void *&#8217; used in arithmetic
include/linux/highmem.h:150: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/var/lib/dkms/nvidia/180.44/build/nv.c: In function &#8216;nvos_proc_create&#8217;:
/var/lib/dkms/nvidia/180.44/build/nv.c:596: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:597: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:598: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:618: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:632: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:643: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:653: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:663: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:674: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c:681: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/var/lib/dkms/nvidia/180.44/build/nv.c: In function &#8216;nvos_proc_add_warning_file&#8217;:
/var/lib/dkms/nvidia/180.44/build/nv.c:708: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
make[3]: *** [/var/lib/dkms/nvidia/180.44/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/180.44/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
```


I think the problem lies with the error "error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;".

would be grateful for help!

---

### Post by KhaaL on 2009-04-09
...small bump...

---

### Post by afv on 2009-04-11
Same problem with 185.19…


From [http://forums.nvidia.com/index.php?act=Print&client=printer&f=33&t=93482](http://forums.nvidia.com/index.php?act=Print&client=printer&f=33&t=93482):

> 
OK, if anyone runs into this problem.

Run:

sh NVIDIA-Linux-x86_64-180.44-pkg2.run -x

That will dump the driver into a directory like:

NVIDIA-Linux-x86_64-180.44-pkg2

go to /usr/src/nv subdirectory inside NVIDIA-Linux-x86_64-180.44-pkg2

Open nv.c in a text editor such as Gedit, locate all instances of "owner" and commend the line out:

Example:

.owner = THIS_MODULE,

becomes

/* .owner = THIS_MODULE, */

Save the file. Install kernel 2.6.29-git8, reboot.

Uninstall your driver like you normally would to make sure none of it is there from your last install.

Navigate to the NVIDIA-Linux-x86_64-180.44-pkg2 wherever you put it:

Become root (su) or prefix this stuff with sudo (Ubuntu)

chmod +x nvidia-installer
./nvidia-installer

It should now install.


---

### Post by KhaaL on 2009-04-11
is it safe to modify nv.c in that manner, isn't there risk of breakage?

---

### Post by hamidoo on 2009-06-11
I had the same problem when i try to install kernel 2.6.30 with nvidia driver 180.40, but after upgrading to nivida drivers ver. 180.53 it worked gr8!

Here is the link to the repository of the new 180.53 drivers:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Install the .53 driver then install the kernel

**Update:** now the current nvidia driver in the repo is 185.18.14 (which is the LATEST official driver from nvidia).
Everything is ok after updating to this driver.

---

### Post by Joshua66 on 2009-06-14
I had the same nvidia problem with 2.6.30 and the following worked for me:
   [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639/comments/8)
Cheers,
Josh

---

### Post by overlordofmu on 2009-07-09
Thank you, [afv]("http://ubuntuforums.org/member.php?u=404801")!

Your suggestion worked perfectly.  Thank you again for finding that information and posting it here.

I would like to add that I am a Gentoo user and not an Ubuntu users but this issue and solution were not specific to a single distribution.

afv - YOU ROCK!

---

