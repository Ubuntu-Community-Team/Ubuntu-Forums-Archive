---
title: "Help! Ubuntu -&gt; VirtualBox -&gt; Guest Additions Problem"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by bwilk87 on 2008-12-05
I am running VirtualBox from Windows Vista and I have Ubuntu installed. I am trying to get my resolution higher since it's at 800x600 right now. I am trying to install Guest Additions and this is what I get...


cd /media/cdrom
sudo bash ./VBoxLinux*

blah blah blah

Building the VirtualBox Guest Additions kernel module...
Unable to build the kernel module. See the log file /var/ blah blah


Any ideas?

---

### Post by littlebat on 2008-12-06
> See the log file /var/
post your installation log file in /var/

I have forgotten the detail of how to install guest additions in ubuntu in the VirtualBox. I remember I have installed linux-headers and build-essential packages to install it.

You can try:
> 
sudo apt-get install linux-headers-$(uname -r) build-essential


---

### Post by freelook on 2008-12-21
I'm having the same trouble as bwilk87.  Does anybody have an answer to this problem?

Installing the linux headers and build-essential didn't seem to help.

---

### Post by Partyboi2 on 2008-12-21
Can you post your var/log/vboxadd-install.log file?

---

### Post by kaapstorm on 2009-03-04
I have the same problem.

My vboxadd-install.log (not included because without Guest Additions I can't copy and paste) complained about a missing "asm/semaphore.h". I sniffed around (sudo apt-get install apt-file; sudo apt-file update; apt-file search semaphore.h) and found it under my kernel source directory.

I symlinked to it from where Guest Additions is looking for it:

> 
  $ cd /usr/src/linux-headers-$(uname -r)/include/asm
  $ sudo ln -s ../linux/semaphore.h


That resolved the first error, but it only got me a little further. My next error comes when trying to build cmc.o. The error is:

```

In file included from /tmp/vbox.3/include/iprt/types.h:72,
                 from /tmp/vbox.3/r0drv/linux/the-linux-kernel.h:25,
                 from /tmp/vbox.3/cmc.c:17:
include/linux/types.h:40: error: redefinition of typedef 'uintptr_t'
/tmp/vbox.3/include/iprt/stdint.h:118: error: previous declaration of 'uintptr_t' was here

```

Hints, anyone?

---

### Post by jackdale on 2010-04-08
> **littlebat said:**
> post your installation log file in /var/

I have forgotten the detail of how to install guest additions in ubuntu in the VirtualBox. I remember I have installed linux-headers and build-essential packages to install it.

You can try:

Same problem here.

As suggested, I tried:
```
sudo apt-get install linux-headers-$(uname -r) build-essential 
```

Here is the /var/log/ file:
```
Installing VirtualBox 3.0.8 Guest Additions, built Fri Oct  2 11:21:38 CEST 2009

Testing the setup of the guest system

Building test kernel module vboxadd_test...

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.32-19-generic/build SUBDIRS=/tmp/selfgz3287/module/test SRCROOT=/tmp/selfgz3287/module/test modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/selfgz3287/module/test/.tmp_versions ; rm -f /tmp/selfgz3287/module/test/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/selfgz3287/module/test
  gcc -Wp,-MD,/tmp/selfgz3287/module/test/.test.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-19-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/lib/modules/2.6.32-19-generic/build/include -I/tmp/selfgz3287/module/test/ -I/tmp/selfgz3287/module/test/include -I/tmp/selfgz3287/module/test/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_WITH_HGCM  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)"  -c -o /tmp/selfgz3287/module/test/.tmp_test.o /tmp/selfgz3287/module/test/test.c
  set -e ; perl /usr/src/linux-headers-2.6.32-19-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "gcc" "ld" "nm" "" "" "1" "/tmp/selfgz3287/module/test/test.o";
  ld -m elf_x86_64   -r -o /tmp/selfgz3287/module/test/vboxadd_test.o /tmp/selfgz3287/module/test/test.o
(cat /dev/null;   echo kernel//tmp/selfgz3287/module/test/vboxadd_test.ko;) > /tmp/selfgz3287/module/test/modules.order
make -f /usr/src/linux-headers-2.6.32-19-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-19-generic/Module.symvers -I /tmp/selfgz3287/module/test/Module.symvers  -o /tmp/selfgz3287/module/test/Module.symvers -S -w  -s
  gcc -Wp,-MD,/tmp/selfgz3287/module/test/.vboxadd_test.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-19-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/lib/modules/2.6.32-19-generic/build/include -I/tmp/selfgz3287/module/test/ -I/tmp/selfgz3287/module/test/include -I/tmp/selfgz3287/module/test/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -D_X86_ -DIN_RT_R0 -DIN_SUP_R0 -DVBGL_VBOXGUEST -DVBGL_HGCM -DVBOX_WITH_HGCM  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vboxadd_test.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test)"  -DMODULE -c -o /tmp/selfgz3287/module/test/vboxadd_test.mod.o /tmp/selfgz3287/module/test/vboxadd_test.mod.c
  ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-19-generic/scripts/module-common.lds --build-id -o /tmp/selfgz3287/module/test/vboxadd_test.ko /tmp/selfgz3287/module/test/vboxadd_test.o /tmp/selfgz3287/module/test/vboxadd_test.mod.o
Inserting the test module module/test/vboxadd_test.ko into the kernel.
Building test kernel module vboxadd_test_drm...

/tmp/selfgz3287/module/test_drm/Makefile.include.header:97: Using BUILD_TYPE='release' from the environment.
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.32-19-generic/build SUBDIRS=/tmp/selfgz3287/module/test_drm SRCROOT=/tmp/selfgz3287/module/test_drm modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/selfgz3287/module/test_drm/.tmp_versions ; rm -f /tmp/selfgz3287/module/test_drm/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/selfgz3287/module/test_drm
/tmp/selfgz3287/module/test_drm/Makefile.include.header:97: Using BUILD_TYPE='release' from the environment.
  gcc -Wp,-MD,/tmp/selfgz3287/module/test_drm/.test_drm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-19-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/lib/modules/2.6.32-19-generic/build/include -I/tmp/selfgz3287/module/test_drm/ -I/tmp/selfgz3287/module/test_drm/include -I/tmp/selfgz3287/module/test_drm/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DVBGL_VBOXGUEST -DVBOX_WITH_HGCM -DLOG_TO_BACKDOOR -DRT_WITH_VBOX -DIN_MODULE -DIN_GUEST_R0 -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(test_drm)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test_drm)"  -c -o /tmp/selfgz3287/module/test_drm/.tmp_test_drm.o /tmp/selfgz3287/module/test_drm/test_drm.c
  set -e ; perl /usr/src/linux-headers-2.6.32-19-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "gcc" "ld" "nm" "" "" "1" "/tmp/selfgz3287/module/test_drm/test_drm.o";
  ld -m elf_x86_64   -r -o /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.o /tmp/selfgz3287/module/test_drm/test_drm.o
(cat /dev/null;   echo kernel//tmp/selfgz3287/module/test_drm/vboxadd_test_drm.ko;) > /tmp/selfgz3287/module/test_drm/modules.order
make -f /usr/src/linux-headers-2.6.32-19-generic/scripts/Makefile.modpost
/tmp/selfgz3287/module/test_drm/Makefile.include.header:97: Using BUILD_TYPE='release' from the environment.
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-19-generic/Module.symvers -I /tmp/selfgz3287/module/test_drm/Module.symvers  -o /tmp/selfgz3287/module/test_drm/Module.symvers -S -w  -s
  gcc -Wp,-MD,/tmp/selfgz3287/module/test_drm/.vboxadd_test_drm.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-19-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/lib/modules/2.6.32-19-generic/build/include -I/tmp/selfgz3287/module/test_drm/ -I/tmp/selfgz3287/module/test_drm/include -I/tmp/selfgz3287/module/test_drm/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DVBGL_VBOXGUEST -DVBOX_WITH_HGCM -DLOG_TO_BACKDOOR -DRT_WITH_VBOX -DIN_MODULE -DIN_GUEST_R0 -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vboxadd_test_drm.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd_test_drm)"  -DMODULE -c -o /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.mod.o /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.mod.c
  ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-19-generic/scripts/module-common.lds --build-id -o /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.ko /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.o /tmp/selfgz3287/module/test_drm/vboxadd_test_drm.mod.o
Attempt to remove old DKMS modules...
  removing module vboxadd version  3.0.8
Done.

Building the VirtualBox Guest Additions kernel module.

Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxadd/3.0.8/source ->
                 /usr/src/vboxadd-3.0.8

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-19-generic -C /lib/modules/2.6.32-19-generic/build M=/var/lib/dkms/vboxadd/3.0.8/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-19-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxadd/3.0.8/build/ for more information.
0
0
ERROR: binary package for vboxadd: 3.0.8 not found
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.32-19-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
  gcc -Wp,-MD,/tmp/vbox.1/.cmc.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-19-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/lib/modules/2.6.32-19-generic/build/include -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DVBGL_VBOXGUEST -DVBOX_WITH_HGCM -DLOG_TO_BACKDOOR -DRT_WITH_VBOX -DIN_MODULE -DIN_GUEST_R0 -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(cmc)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxadd)"  -c -o /tmp/vbox.1/.tmp_cmc.o /tmp/vbox.1/cmc.c
/tmp/vbox.1/cmc.c: In function ‘vboxadd_hgcm_callback’:
/tmp/vbox.1/cmc.c:34: error: ‘TASK_UNINTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vbox.1/cmc.c:34: error: (Each undeclared identifier is reported only once
/tmp/vbox.1/cmc.c:34: error: for each function it appears in.)
/tmp/vbox.1/cmc.c:34: error: implicit declaration of function ‘schedule’
/tmp/vbox.1/cmc.c:36: error: implicit declaration of function ‘schedule_timeout’
/tmp/vbox.1/cmc.c: In function ‘vboxadd_hgcm_callback_interruptible’:
/tmp/vbox.1/cmc.c:45: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vbox.1/cmc.c:45: error: implicit declaration of function ‘signal_pending’
make[2]: *** [/tmp/vbox.1/cmc.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make: *** [vboxadd] Error 2
```

Not sure of where to go from here...
Works well in Mac OS X under Fusion 2
But currently trying to do it from amd64 Ubuntu 9.10 with VirtualBox

---

