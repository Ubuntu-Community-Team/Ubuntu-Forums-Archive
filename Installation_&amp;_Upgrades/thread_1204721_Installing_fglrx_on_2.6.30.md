---
title: "Installing fglrx on 2.6.30"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by voy on 2009-07-05
Hey,

So I have been forced to install 2.6.30 kernel, because otherwise Opera keeps timing out on ipv6 dns queries. Trouble is, my fglrx stopped working.

I tried both using the fglrx-kernel-source package with the following results:

```

voy@apocalypse:~$ sudo apt-get install fglrx-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xorg-driver-fglrx
The following NEW packages will be installed:
  fglrx-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/1609kB of archives.
After this operation, 5427kB of additional disk space will be used.
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 160973 files and directories currently installed.)
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.620-0ubuntu1~jaunty_i386.deb) ...
Setting up fglrx-kernel-source (2:8.620-0ubuntu1~jaunty) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.30-10-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.620/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.30-10-generic (i686) first.
Done.

```

So I took a look at the logs in /var/lib/dkms/fglrx/8.620/build/ and this is what I found out:

```
voy@apocalypse:/var/lib/dkms/fglrx/8.620/build$ sudo ./make.sh
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.30-10-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.620/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-10-generic'
  CC [M]  /var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:41:2: error: #error unknown or undefined architecture configured
In file included from /var/lib/dkms/fglrx/8.620/build/2.6.x/drmP.h:86,
                 from /var/lib/dkms/fglrx/8.620/build/2.6.x/drm_proc.h:41,
                 from /var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:431:
/var/lib/dkms/fglrx/8.620/build/2.6.x/drm_os_linux.h:45: error: conflicting types for &#8216;irqreturn_t&#8217;
include/linux/irqreturn.h:16: error: previous declaration of &#8216;irqreturn_t&#8217; was here
In file included from /var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:431:
/var/lib/dkms/fglrx/8.620/build/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:1230: warning: unused variable &#8216;ret&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:1229: warning: unused variable &#8216;i&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c: In function &#8216;KCL_GetEffectiveUid&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:1451: error: &#8216;struct task_struct&#8217; has no member named &#8216;euid&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c: In function &#8216;KCL_PosixSecurityCapSetIPCLock&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:1825: error: &#8216;struct task_struct&#8217; has no member named &#8216;cap_effective&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:1829: error: &#8216;struct task_struct&#8217; has no member named &#8216;cap_effective&#8217;
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c: In function &#8216;KCL_InstallInterruptHandler&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:2727: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c: In function &#8216;KAS_Ih_Execute&#8217;:
/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.c:4209: warning: &#8216;return&#8217; with no value, in function returning non-void
make[2]: *** [/var/lib/dkms/fglrx/8.620/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.620/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-10-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

```

Obviously, there is some sort of a problem with the compilation, but is it something that I can solve or is it just that fglrx is incompatible with my kernel? I don't insist on 2.6.30, the thing is that kernels below 2.6.29 (I think) don't support the option to disable ipv6 compiled in the kernel and I need to do that to run Opera as my main browser.

Thanks for any pointers!

---

### Post by excsniper on 2009-07-05
sup voy,
i've been F5ing on this thread for a while now cuz i had the same problem: love opera, hate ipv6 :)

after reinstalling the new kernal+ubuntu twice i decided to give up..
then it i thought maybe the driver doesn't support the new kernel because there have been cases like that before... so here's the solution for ur problem:

use the 2.6.28 kernal but compile it urself. before u compile, make sure u config it so that it doesn't include **ipv6 protocol**.

glhf
spave(sniper)

---

### Post by voy on 2009-07-06
Trouble is, I am not sure how to compile the kernel exactly as it is in Jaunty, only minus ipv6. Is there any kind of tutorial I could use?

---

### Post by excsniper on 2009-07-06
ofc just google around for a tut.
err maybe ill just link u:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

u can skip step 1 and 1.1
when it asks u to use "**make menuconfig**" in step 5, use "**make xconfig**" instead.
a window with alot of options will popup. now **Ctrl+F** and enter "**ipv6**" scroll down to where it says "**The IPv6 Protocol**" and **uncheck it**. Then press **Ctrl+S**, close the window and refer back to the tut.

make sure u "sudo" everything!

glhf
Spave
ps: if step 6 gives u "nothing to be done", u can try:
[B]fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
[/B]pps: make sure u use 2.6.28...

---

### Post by chuck_notorious on 2009-07-29
I have the same problem except I'm running a 2.6.29 kernel that I compiled to get realtime support.

I wonder if there are any solutions to this other than downgrading the kernel. I thought I was through with kernel compiles for the moment!

--Charles.

---

### Post by chuck_notorious on 2009-07-29
Posts on [phoronix forums]("http://www.phoronix.com/forums/forumdisplay.php?f=19") suggest that current versions of fglrx are incompatible with new kernels (2.6.29/30). There patches but I couldn't get it to work.

--C

---

