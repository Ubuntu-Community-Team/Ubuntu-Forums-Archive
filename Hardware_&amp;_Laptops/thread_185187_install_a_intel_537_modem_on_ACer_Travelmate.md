---
title: "install a intel 537 modem on ACer Travelmate"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by caven80 on 2006-05-31
Hey...

I hav been trying to install a intel 537 modem for a while now but to no avail.
i think i hav come close to installing it though, considering i hav atleast found the right drivers and commands to move forward ( i'm a newbie to linux/ubuntu)

The build essentials and linux headers seem to be up to date...also successfully installed GCC 3.4 .(all 3 pakages) but had more trouble installing da modem..
i am pasting da log. Log includes- from installing GCC to trying to issue 'make install' commands..

Please help further.

Many Thanks..

Caven
************************************************** ********

root@regonet:/modem# ls -la 
total 2324
dr-xr-xr-x 2 root root 4096 Feb 15 23:16 .
drwxr-xr-x 26 root root 4096 Feb 17 16:40 ..
-r-xr-xr-x 1 root root 1707096 Feb 15 23:16 cpp-3.4_3.4.4-6ubuntu8_i386.deb
-r-xr-xr-x 1 root root 163028 Feb 15 23:15 gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
-r-xr-xr-x 1 root root 484408 Feb 15 23:13 gcc-3.4_3.4.4-6ubuntu8_i386.deb


root@regonet:/modem# dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.debSelecting previously deselected package cpp-3.4.
(Reading database ... 72542 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.4-6ubuntu8_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu ...
Setting up cpp-3.4 (3.4.4-6ubuntu ...
Setting up gcc-3.4 (3.4.4-6ubuntu ...

root@regonet:/modem# cd /intel*

root@regonet:/intel-537EP_secure-2.60.80.1# make clean
cd coredrv; make clean
make[1]: Entering directory `/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko

root@regonet:/intel-537EP_secure-2.60.80.1# make 537

Module precompile check
Current running kernel is: 2.6.12-9-386
/lib/modules... autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
version.h matches running kernel
2.6.12-9-386
make[1]: Entering directory `/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: type defaults to `int' in declaration of `EXPORT_SYMBOL_NOVERS'
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `open':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:394: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `close':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:416: warning: `pm_unregister' is deprecated (declared at include/linux/pm.h:111)
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `hamproc_write':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:660: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: At top level:
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:754: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:755: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `kScheduleDPC':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:861: warning: implicit declaration of function `pm_access'
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/intel-537EP_secure-2.60.80.1/coredrv/coredrv.c:877: warning: function declaration isn't a prototype
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/clmmain.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/rts.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/task.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/uart.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/wwh_dflt.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/locks.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/softserial_io.o
/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.c: In function `softserial_write':
/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.c:94: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/softserial_ioctl.o
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/softserial.o
/intel-537EP_secure-2.60.80.1/coredrv/softserial.c: In function `softserial_register_tty':
/intel-537EP_secure-2.60.80.1/coredrv/softserial.c:141: warning: assignment from incompatible pointer type
CC [M] /intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.o
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:48: warning: function declaration isn't a prototype
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:65: warning: function declaration isn't a prototype
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: In function `afe_Write':
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:417: warning: ignoring return value of `copy_from_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: In function `afe_Read':
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:437: warning: ignoring return value of `copy_to_user', declared with attribute warn_unused_result
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c: At top level:
/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.c:454: warning: initialization from incompatible pointer type
LD [M] /intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
Building modules, stage 2.
MODPOST
Warning: could not find /intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /intel-537EP_secure-2.60.80.1/coredrv/537core.lib
*** Warning: "pm_access" [/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko] undefined!
CC /intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
LD [M] /intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: Leaving directory `/intel-537EP_secure-2.60.80.1/coredrv'

root@regonet:/intel-537EP_secure-2.60.80.1# make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.12-9-386
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modulesdone
root@regonet:/intel-537EP_secure-2.60.80.1#

---

