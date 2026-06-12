---
title: "Strange bug in 8.10"
date: 2008-11-07
forum: General Help
---

### Post by Brunno Silva on 2008-11-07
I have 2 computers, both with an upgraded 8.10 Ubuntu. They seem to share the same little bugs, for example, a problem in window rendering. All of them are simple things, so I'm not worried. One bug in particular, however, is quite disturbing and it only happens in my laptop (maybe, because its a AMD 64 bits).

The bug happens during startup, shortly after Gnome loading. The startup (and the startup progress bar) simply freezes! I need to press some key to "force" it continue (?), otherwise it keeps in this bizarre state forever. In some rare cases, the keyboard stops working, so I need to restart and repeat the very same process. The shutdown has a similar situation. Do you have any workaround while someone doesn't fix this issue?

Cheers,
Brunno Silva

---

### Post by Brunno Silva on 2008-11-08
No ideas?

---

### Post by Lesouteneur on 2008-11-08
This is my problem too and there is a couple of other threads I am subscribed to:

[http://ubuntuforums.org/showthread.php?t=975080](http://ubuntuforums.org/showthread.php?t=975080)
[http://ubuntuforums.org/showthread.php?t=972910](http://ubuntuforums.org/showthread.php?t=972910)
[http://ubuntuforums.org/showthread.php?t=968663](http://ubuntuforums.org/showthread.php?t=968663)

Would you happen to have an HP/Compaq computer?

---

### Post by Brunno Silva on 2008-11-10
Exactly. Its a HP Pavillion notebook.

---

### Post by Brunno Silva on 2008-11-10
By the way, another big problem just arise: My VirtualBox doesn't works. When I start it, the following message appears:> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 0x80004005
Component: Console
Interface: IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}I did re-setup, but...> brunno@brunno-laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrongAnd then...> Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.4/source ->
                 /usr/src/vboxdrv-1.6.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/vboxdrv/1.6.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions ; rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
In file included from /tmp/vbox.2/linux/SUPDrv-linux.c:35:
/tmp/vbox.2/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.2/linux/SUPDrv-linux.c: In function &#8216;supdrvOSGipResume&#8217;:
/tmp/vbox.2/linux/SUPDrv-linux.c:1331: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vboxdrv] Error 2

---

### Post by Brunno Silva on 2008-11-10
By the way, another big problem just arise: My VirtualBox doesn't works. When I start it, the following message appears:> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 0x80004005
Component: Console
Interface: IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}I did re-setup, but...> brunno@brunno-laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrongAnd then...> Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.4/source ->
                 /usr/src/vboxdrv-1.6.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-7-generic -C /lib/modules/2.6.27-7-generic/build M=/var/lib/dkms/vboxdrv/1.6.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions ; rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-7-generic/build/include -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
In file included from /tmp/vbox.2/linux/SUPDrv-linux.c:35:
/tmp/vbox.2/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.2/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.2/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vboxdrv] Error 2

---

### Post by Lesouteneur on 2008-11-10
Are you sure you have added yourself to the vbox user group? If you haven't, go to *Administration>users and groups*. There you can add yourself.

---

### Post by Brunno Silva on 2008-11-10
Yes, my user is a member of the vbox user group. The VirtualBox was working fine just before the upgrade.

---

### Post by Brunno Silva on 2008-11-12
So... Should I suppose both problems won't have any solution soon?

---

### Post by m.srivathsan on 2008-11-13
Hi,

Regarding the VirtualBox problem, it was solved after I uninstalled KVM which again got installed when I upgraded from 8.04 to 8.10.  Also, VirtualBox asked to do some kind of a "recompilation" of kernel modules - I just followed the advice on one of it's Message Boxes - really don't remember exact - sorry for that

Thanks and rgds,
Watson

---

### Post by iponeverything on 2008-11-13
If you poke around launchpad you'll find this bug.  It never hurts to add your two cents, it might be the piece they need to squash it.

---

### Post by Lesouteneur on 2008-11-20
Josueped solved my problem for me you just have to add the boot option "acpi=noirq" (without quotes):

> **Josueped said:**
> here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

---

