---
title: "Please update your driver (Adaptec raid)"
date: 2020-11-17
forum: Hardware
---

### Post by David_Partridge on 2020-11-17
Lubuntu 20.04.1  Adaptec aacraid driver 1.2.1[50877]-custom 

Based on the 50877 version number that driver dates back to 2016!!!

Reported a problem to Microsemi who responded: Please update your driver and pointed me to 

[https://storage.microsemi.com/en-us/downloads/linux_source/linux_source_code/productid=asr-8885&dn=adaptec+raid+8885.php](https://storage.microsemi.com/en-us/downloads/linux_source/linux_source_code/productid=asr-8885&dn=adaptec+raid+8885.php)

which is driver 1.2.1-59002 

I haven't a clue how I can do that I'm now here asking what I need to do to get that done (ideally by you guys and gals at Canonical).

David

---

### Post by CelticWarrior on 2020-11-17
Download the DKMS one, extract it and inside you'll find a deb folder with a deb file inside. Install like any other deb.

---

### Post by Yellow Pasque on 2020-11-17
> **David_Partridge said:**
> (ideally by you guys and gals at Canonical).

This is a forum of users supporting users. Canonical is a relatively small operation and their employees are busy developing and reading bug reports.

---

### Post by David_Partridge on 2020-11-17
Hmmm

```
root@charon:/home/amonra/Downloads/adaptec/aacraid-dkms-1.2.1.59002/deb# dpkg -i aacraid-dkms_1.2.1.59002_all.deb 
Selecting previously unselected package aacraid-dkms.
(Reading database ... 375604 files and directories currently installed.)
Preparing to unpack aacraid-dkms_1.2.1.59002_all.deb ...
Unpacking aacraid-dkms (1.2.1.59002) ...
Setting up aacraid-dkms (1.2.1.59002) ...
Loading new aacraid-1.2.1.59002 DKMS files...
Building for 5.4.0-54-generic
Building for architecture x86_64
Building initial module for 5.4.0-54-generic
ERROR (dkms apport): unable to determine source package for aacraid-dkms
Error! Bad return status for module build on kernel: 5.4.0-54-generic (x86_64)
Consult /var/lib/dkms/aacraid/1.2.1.59002/build/make.log for more information.
dpkg: error processing package aacraid-dkms (--install):
 installed aacraid-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 aacraid-dkms
root@charon:/home/amonra/Downloads/adaptec/aacraid-dkms-1.2.1.59002/deb# 


```

```
DKMS make.log for aacraid-1.2.1.59002 for kernel 5.4.0-54-generic (x86_64)
Tue 17 Nov 19:45:21 GMT 2020
make: Entering directory '/usr/src/linux-headers-5.4.0-54-generic'
  AR      /var/lib/dkms/aacraid/1.2.1.59002/build/built-in.a
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/linit.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/aachba.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/commctrl.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/comminit.o
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:68:10: fatal error: linux/pci-aspm.h: No such file or directory
   68 | #include <linux/pci-aspm.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[1]: *** [scripts/Makefile.build:275: /var/lib/dkms/aacraid/1.2.1.59002/build/linit.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c: In function ‘aac_scsi_cmd’:
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c:4720:28: warning: this statement may fall through [-Wimplicit-f>
 4719 |      if (!(dev->raw_io_interface) ||
      |          ~~~~~~~~~~~~~~~~~~~~~~~~~~~
 4720 |          !(dev->raw_io_64) ||
      |          ~~~~~~~~~~~~~~~~~~^~
 4721 |          ((scsicmd->cmnd[1] & 0x1f) != SAI_READ_CAPACITY_16))
      |          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c:4724:5: note: here
 4724 |     case INQUIRY:
      |     ^~~~
make: *** [Makefile:1757: /var/lib/dkms/aacraid/1.2.1.59002/build] Error 2
make: Leaving directory '/usr/src/linux-headers-5.4.0-54-generic'



```

---

### Post by David_Partridge on 2020-11-17
I hacked past that by editing linit.c in /usr/src/aacraid-1.2.1.59002/ to include pci.h instead of pci-aspm.h

But then got:

```
DKMS make.log for aacraid-1.2.1.59002 for kernel 5.4.0-54-generic (x86_64)
Tue 17 Nov 20:34:46 GMT 2020
make: Entering directory '/usr/src/linux-headers-5.4.0-54-generic'
  AR      /var/lib/dkms/aacraid/1.2.1.59002/build/built-in.a
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/aachba.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/linit.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/commctrl.o
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/comminit.o
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c: In function ‘aac_scsi_cmd’:
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c:4720:28: warning: this statement may fall through [-Wimplicit-fallthrough=]
 4719 |      if (!(dev->raw_io_interface) ||
      |          ~~~~~~~~~~~~~~~~~~~~~~~~~~~
 4720 |          !(dev->raw_io_64) ||
      |          ~~~~~~~~~~~~~~~~~~^~
 4721 |          ((scsicmd->cmnd[1] & 0x1f) != SAI_READ_CAPACITY_16))
      |          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/aacraid/1.2.1.59002/build/aachba.c:4724:5: note: here
 4724 |     case INQUIRY:
      |     ^~~~
  CC [M]  /var/lib/dkms/aacraid/1.2.1.59002/build/commsup.o
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c: In function ‘aac_fib_debug_print’:
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:952:2: error: implicit declaration of function ‘do_gettimeofday’; did you mean ‘do_settimeofday64’? [-Werror=implicit-function-declaration]
  952 |  do_gettimeofday(&now);
      |  ^~~~~~~~~~~~~~~
      |  do_settimeofday64
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c: At top level:
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2514:14: error: initialization of ‘int (*)(struct scsi_device *, unsigned int,  void *)’ from incompatible pointer type ‘int (*)(struct scsi_device *, int,  void *)’ [-Werror=incompatible-pointer-types]
 2514 |  .ioctl    = aac_ioctl,
      |              ^~~~~~~~~
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2514:14: note: (near initialization for ‘aac_driver_template.ioctl’)
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2518:20: error: initialization of ‘int (*)(struct scsi_device *, unsigned int,  void *)’ from incompatible pointer type ‘int (*)(struct scsi_device *, int,  void *)’ [-Werror=incompatible-pointer-types]
 2518 |  .compat_ioctl   = aac_compat_ioctl,
      |                    ^~~~~~~~~~~~~~~~
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2518:20: note: (near initialization for ‘aac_driver_template.compat_ioctl’)
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2558:3: error: ‘struct scsi_host_template’ has no member named ‘use_clustering’
 2558 |  .use_clustering   = ENABLE_CLUSTERING,
      |   ^~~~~~~~~~~~~~
/var/lib/dkms/aacraid/1.2.1.59002/build/linit.c:2558:22: error: ‘ENABLE_CLUSTERING’ undeclared here (not in a function)
 2558 |  .use_clustering   = ENABLE_CLUSTERING,
      |                      ^~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[1]: *** [scripts/Makefile.build:275: /var/lib/dkms/aacraid/1.2.1.59002/build/linit.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/var/lib/dkms/aacraid/1.2.1.59002/build/commsup.c: In function ‘aac_fib_alloc’:
/var/lib/dkms/aacraid/1.2.1.59002/build/commsup.c:452:3: error: implicit declaration of function ‘do_gettimeofday’; did you mean ‘do_settimeofday64’? [-Werror=implicit-function-declaration]
  452 |   do_gettimeofday(&now);
      |   ^~~~~~~~~~~~~~~
      |   do_settimeofday64
cc1: some warnings being treated as errors
make[1]: *** [scripts/Makefile.build:273: /var/lib/dkms/aacraid/1.2.1.59002/build/commsup.o] Error 1
make: *** [Makefile:1757: /var/lib/dkms/aacraid/1.2.1.59002/build] Error 2
make: Leaving directory '/usr/src/linux-headers-5.4.0-54-generic'


```

At which point I threw in the towel!

David

---

### Post by guiverc on 2020-11-17
> **David_Partridge said:**
> Lubuntu 20.04.1  Adaptec aacraid driver 1.2.1[50877]-custom 

I haven't a clue how I can do that I'm now here asking what I need to do to get that done (ideally by you guys and gals at Canonical).

David

This is mostly a support site.

For bugs and requests to update packages, a bug needs to be filed on launchpad.

Refer [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

A bug report maybe seen by the *guys and gals at Canonical*, where I suspect none have seen your post here.

---

