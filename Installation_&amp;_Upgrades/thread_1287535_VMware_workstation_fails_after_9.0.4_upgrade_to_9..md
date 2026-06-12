---
title: "VMware workstation fails after 9.0.4 upgrade to 9.10"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by dverhoeven on 2009-10-10
Hi,

just upgraded to ubuntu 9.10 from 9.0.4.
before I used a script after each kernel upgrade, but now it fails:

#!/bin/bash

cd ~
rm -rf vmware-modules
mkdir vmware-modules
cd vmware-modules
find /usr/lib/vmware/modules/source -name "*.tar" -exec tar xf '{}' \;
mkdir -p /lib/modules/`uname -r`/misc
rm -f /lib/modules/`uname -r`/misc{vmblock.ko,vmci.ko,vmmon.ko,vmnet.ko,vsock.ko}
cd vmblock-only; make; cd ..; cp -p vmblock.o /lib/modules/`uname -r`/misc/vmblock.ko
cd vmci-only; make; cd ..; cp -p vmci.o /lib/modules/`uname -r`/misc/vmci.ko
cd vmmon-only; make; cd ..; cp -p vmmon.o /lib/modules/`uname -r`/misc/vmmon.ko
cd vmnet-only; make; cd ..; cp -p vmnet.o /lib/modules/`uname -r`/misc/vmnet.ko
#cd vmppuser-only; make; cd ..; cp -p vmppuser.o /lib/modules/`uname -r`/misc/vmppuser.ko
cd vsock-only; make; cd ..; cp -p vsock.o /lib/modules/`uname -r`/misc/vsock.ko
depmod -a
service vmware restart

output of script (snippet)

Using 2.6.x kernel build system.
make -C /lib/modules/2.6.31-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-12-generic'
  CC [M]  /home/dimitri/vmware-modules/vmblock-only/linux/block.o
In file included from /home/dimitri/vmware-modules/vmblock-only/linux/os.h:35,
                 from /home/dimitri/vmware-modules/vmblock-only/linux/block.c:26:
/home/dimitri/vmware-modules/vmblock-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /home/dimitri/vmware-modules/vmblock-only/linux/vmblockInt.h:40,
                 from /home/dimitri/vmware-modules/vmblock-only/linux/block.c:29:
/home/dimitri/vmware-modules/vmblock-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
make[2]: *** [/home/dimitri/vmware-modules/vmblock-only/linux/block.o] Error 1
make[1]: *** [_module_/home/dimitri/vmware-modules/vmblock-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-12-generic'
make: *** [vmblock.ko] Error 2
cp: cannot stat `vmblock.o': No such file or directory


Would anyone know if it is possible to get the version up and running on 9.1.0 ?

---

### Post by noelvh on 2009-10-10
I am not sure if I can help but in the past when I used VMware, I was forced to do a complete reinstall of the VMware software. This is one of the reasons I use Vbox now. I could not get the kernel modules to work. Once I had to completely reinstall to get it to work. Try removing VMware and installing the version for 9.10

Noel

---

### Post by slakkie on 2009-10-10
I always used this script when I upgraded a kernel:
```

#!/usr/bin/env bash

# Installing kernel header files
echo -e "Installing kernel header files\n"
sleep 5
sudo aptitude install linux-headers-$(uname -r)
echo -e "Making sure vmware is happy, so lets reconfigure it, accept the defaults please\n\n"
sleep 5
sudo /opt/vmware/vmware-config.pl

```

Maybe adjust it a bit (location of vmware-config.pl) but it should still work.

---

### Post by dverhoeven on 2009-10-11
Hi,

thanks for the answers. I have no vmware-config.pl anymore (that was how I did it in the past as well)

I tried to install VMware 6.5.2, but still no go.

It tells me it needs to recompile. This fails, and when looking in the logs, I see not much to hold on to:

Oct 11 16:51:34.487: app| Log for VMware Workstation pid=13840 version=6.5.2 build=build-156735 option=Release
Oct 11 16:51:34.487: app| Host codepage=UTF-8 encoding=UTF-8
Oct 11 16:51:34.487: app| Logging to /tmp/vmware-root/setup-13840.log
Oct 11 16:51:35.486: app| Extracting the sources of the vmmon module.
Oct 11 16:51:35.498: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-12-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1



When I go into the tmp directory where modules are being built, and I manually run sudo make, I get the same errors :




Using 2.6.x kernel build system.
make -C /lib/modules/2.6.31-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-12-generic'
  CC [M]  /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:70: note: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:99:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:119:
/tmp/vmware-root-3285238863/modules/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverSyncCallOnEachCPU&#8217;:
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function &#8216;smp_call_function&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;euid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;egid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root-3285238863/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-12-generic'
make: *** [vmmon.ko] Error 2

---

### Post by dverhoeven on 2009-10-11
In file compat_wait.h (line 78) I found this. My guess is some kind of lib got loaded that aslo contains poll_initwait, but it might be differetn from what is expected. But here I am on slippery territory, maybe someone with more knowledge of programming could say something about this. 

/* If prototype does not match, build will abort here */
extern void poll_initwait(compat_poll_wqueues *);

#define compat_poll_initwait(wait, table) ( \
   (wait) = (table), \
   poll_initwait(wait) \
)

#define compat_poll_freewait(wait, table) ( \
   poll_freewait((table)) \
)

---

### Post by NDLunchbox on 2009-11-10
[http://communities.vmware.com/thread/221724?start=0&amp;tstart=0](http://communities.vmware.com/thread/221724?start=0&amp;tstart=0)

The above thread contains a patch that fixed the issue for me.

---

### Post by ivan.warrer on 2009-11-10
Hi

Maybe this could help you.

search for this *patch vmware-update-2.6.27-5.5.7-2*.tar.gz 
unpack the file.
rerun your vmware-install.pl and (stop when it comes to config.pl (say no).
then go to the directory for the patch vmware-update-2.6.27-5.5.7-2 and run 
./runme.pl

/ivan


> **dverhoeven said:**
> Hi,

thanks for the answers. I have no vmware-config.pl anymore (that was how I did it in the past as well)

I tried to install VMware 6.5.2, but still no go.

It tells me it needs to recompile. This fails, and when looking in the logs, I see not much to hold on to:

Oct 11 16:51:34.487: app| Log for VMware Workstation pid=13840 version=6.5.2 build=build-156735 option=Release
Oct 11 16:51:34.487: app| Host codepage=UTF-8 encoding=UTF-8
Oct 11 16:51:34.487: app| Logging to /tmp/vmware-root/setup-13840.log
Oct 11 16:51:35.486: app| Extracting the sources of the vmmon module.
Oct 11 16:51:35.498: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-12-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1



When I go into the tmp directory where modules are being built, and I manually run sudo make, I get the same errors :




Using 2.6.x kernel build system.
make -C /lib/modules/2.6.31-12-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-12-generic'
  CC [M]  /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:99:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root-3285238863/modules/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:119:
/tmp/vmware-root-3285238863/modules/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-root-3285238863/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root-3285238863/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-12-generic'
make: *** [vmmon.ko] Error 2

---

### Post by dverhoeven on 2009-11-17
Hi, thank you all for taking the time to read and react. 
I can confirm that the vmware patch script fixed the issue, and vmware is running again.

Many thanks

---

