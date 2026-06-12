---
title: "HighPoint RocketRaid 2640 driver"
date: 2011-10-07
forum: Hardware
---

### Post by krutoileshii on 2011-10-07
How I've gotten the RocketRaid 2640x4 driver to compile under 3.0 kernel.

Initially I've followed the steps outlined on the  [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid). However, it still failed to compile due to checks for the kernel version which required additional modifications to the Madefile.def located in the "inc" folder and install.sh files. Below I will outline the steps required to compile the driver.

[LIST=1]
[*]Dowload the open source driver form the HighPoint website (cur ver. 1.3) [http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz](http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz)
[*]Extract the driver to your home directory
[*]Open the Makefile.def located in the /inc/linux folder
[*] Replace the following:

This
```

KERNEL_VER := 2.$(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/linux/version.h | cut -d\  -f3` / 256 % 256)

```
With 
```

KERNEL_VER := $(shell uname -r | cut -f1-2 -d.)

```

This
```

ifneq ($(KERNEL_VER), 2.6)

ifneq ($(KERNEL_VER), 2.4)

$(error Only kernel 2.4/2.6 is supported but you use $(KERNEL_VER))

endif

endif

```

With 

```

ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 3.0)
ifneq ($(KERNEL_VER), 2.4)
$(error Only kernel 2.4/2.6/3.0 is supported but you use $(KERNEL_VER))
endif
endif
endif

```

This

```

ifeq ($(KERNEL_VER), 2.6)

```

With 

```

ifeq ($(KERNEL_VER), $(filter $(KERNEL_VER),3.0 2.6))

```

Save the file.
[*] Open os_linux.h and remove the linux/config.h include statement
[*] Open os_linux.c file and change the follwing

From
```

blkdev_get(bdev, FMODE_READ)

```

To
```

blkdev_get(bdev, FMODE_READ, NULL)

```
Save.
[*] Open osm_linux.c and change the following:

From 

```

static int hpt_queuecommand (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *))

```

to 

```

static int hpt_queuecommand_lck (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *)) 

```

Before the hpt_reset method, insert the lines below:
```

#ifdef DEF_SCSI_QCMD
DEF_SCSI_QCMD(hpt_queuecommand)
#else
#define hpt_queuecommand hpt_queuecommand_lck
#endif

```
Save.

[*]Open install.sh and change section below from:
 
```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac

```

to 

```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
	3.0 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac


```
[/LIST]

The driver should compile and install properly after that. 


I know that some of these things could be automated with a patch program, but i have no clue how to do it. if anyone is willing to tackle it, or help me write it, please send me an e-mail.


Hope this helps other people.

---

### Post by krutoileshii on 2011-10-07
I'll be trying again later on today see if I could manage to get it working.

---

### Post by buffalojr on 2011-10-19
Works for highpoint rr640 series. Did get one warning but the install went through just fine (see below), after which doing a "sudo modprobe rr64x brought everything back.



george@george:~/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/os_linux.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/osm_linux.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/div64.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/hptinfo.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/config.o
  LD [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/rr64x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/.him_magni.o.cmd for /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/him_magni.o
  LD [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/rr64x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
You made a module which is for current kernel 3.0.0-12-generic.
Deleting previous installed driver module rr64x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
backup /boot/initrd.img-3.0.0-12-generic to /boot/initrd.img-3.0.0-12-generic.rr64x.

---

### Post by krutoileshii on 2011-10-19
> **buffalojr said:**
> Works for highpoint rr640 series. Did get one warning but the install went through just fine (see below), after which doing a "sudo modprobe rr64x brought everything back.



george@george:~/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/os_linux.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/osm_linux.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/div64.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/hptinfo.o
  CC [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/config.o
  LD [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/rr64x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/.him_magni.o.cmd for /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/him_magni.o
  LD [M]  /home/george/Downloads/rr64x-linux-src-v1.0/product/rr64x/linux/.build/rr64x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
You made a module which is for current kernel 3.0.0-12-generic.
Deleting previous installed driver module rr64x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
backup /boot/initrd.img-3.0.0-12-generic to /boot/initrd.img-3.0.0-12-generic.rr64x.
I'm working on trying to get this to work with dkms. Right now the install and patch scripts delete the compiled modules provided by highpoint. Once, I get this figured out, and remove the 2.4 checks, i will be posting an update to the above procedures.

---

### Post by bvanaerde on 2011-11-14
I'm having the same problem with my RocketRaid 1740. Just applied your changes to the install files, and it managed to install well.
Now I'm going to reboot, I really hope this will work!

krutoileshii, you are my hero!

---

### Post by Despotism on 2011-11-14
> **krutoileshii said:**
> How I've gotten the RocketRaid 2640x4 driver to compile under 3.0 kernel.

Initially I've followed the steps outlined on the  [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid). However, it still failed to compile due to checks for the kernel version which required additional modifications to the Madefile.def located in the "inc" folder and install.sh files. Below I will outline the steps required to compile the driver.

[LIST=1]
[*]Dowload the open source driver form the HighPoint website (cur ver. 1.3) [http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz](http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz)
[*]Extract the driver to your home directory
[*]Open the Makefile.def located in the /inc/linux folder
[*] Replace the following:

This
```

KERNEL_VER := 2.$(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/linux/version.h | cut -d\  -f3` / 256 % 256)

```
With 
```

KERNEL_VER := $(shell uname -r | cut -f1-2 -d.)

```

This
```

ifneq ($(KERNEL_VER), 2.6)

ifneq ($(KERNEL_VER), 2.4)

$(error Only kernel 2.4/2.6 is supported but you use $(KERNEL_VER))

endif

endif

```

With 

```

ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 3.0)
ifneq ($(KERNEL_VER), 2.4)
$(error Only kernel 2.4/2.6/3.0 is supported but you use $(KERNEL_VER))
endif
endif
endif

```

This

```

ifeq ($(KERNEL_VER), 2.6)

```

With 

```

ifeq ($(KERNEL_VER), $(filter $(KERNEL_VER),3.0 2.6))

```

Save the file.
[*] Open os_linux.h and remove the linux/config.h include statement
[*] Open os_linux.c file and change the follwing

From
```

blkdev_get(bdev, FMODE_READ)

```

To
```

blkdev_get(bdev, FMODE_READ, NULL)

```
Save.
[*] Open osm_linux.c and change the following:

From 

```

static int hpt_queuecommand (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *))

```

to 

```

static int hpt_queuecommand_lck (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *)) 

```

Before the hpt_reset method, insert the lines below:
```

#ifdef DEF_SCSI_QCMD
DEF_SCSI_QCMD(hpt_queuecommand)
#else
#define hpt_queuecommand hpt_queuecommand_lck
#endif

```
Save.

[*]Open install.sh and change section below from:
 
```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac

```

to 

```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
	3.0 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac


```
[/LIST]

The driver should compile and install properly after that. 


I know that some of these things could be automated with a patch program, but i have no clue how to do it. if anyone is willing to tackle it, or help me write it, please send me an e-mail.


Hope this helps other people.

Awesome... I could have saved myself a lot of time and effort if I had performed a google search :)

This does work for Ubuntu 11.10 AMD 64x as well.
You can also run it with dkms by following the ending part of the RocketRaid instructional


From the original page with my edits on it.
Configure dkms.conf
Back in the "root" rr64x-linux-src-v1.0/, we create dkms.conf and open it in our favorite text editor:


# ls
    inc  lib  osm  product  README
# touch dkms.conf #create dkms.conf file
# texteditorofyourchoice dkms.conf

Inside dkms.conf, we add the lines:

MAKE="make -C product/rr64x/linux/ KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr64x/linux/ clean"
BUILT_MODULE_NAME=rr64x
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr64x/linux/
PACKAGE_NAME=rr64x
PACKAGE_VERSION=1.0
AUTOINSTALL=yes
REMAKE_INITRD=yes

Tell DKMS about the module

# ls
    dkms.conf  inc  lib  osm  product  README
# sudo cp -R . /usr/src/rr64x-1.0
# sudo dkms add -m rr64x -v 1.0
    dkms does its thing..

Build and Install
# sudo dkms build -m rr64x -v 1.0
    dkms does its thing.... watch for build errors... you may need to tweak dkms.conf
# sudo dkms install -m rr64x -v 1.0
    dkms does its thing.... module is copied into current kernel module tree

# sudo gedit /etc/initramfs-tools/modules
Add to the end of the file
rr64x
Save/Exit

The only thing I could get to the work was creating a deb file to do the whole thing..

# sudo dkms mkdeb -m rr64x -v 1.0

I get this error:

rr64x-linux-src-v1.0$ sudo dkms mkdeb -m rr64x -v 1.0
Package `debhelper' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Using /etc/dkms/template-dkms-mkdeb
copying template...
modifying debian/changelog...
modifying debian/compat...
modifying debian/control...
modifying debian/copyright...
modifying debian/dirs...
modifying debian/postinst...
modifying debian/prerm...
modifying debian/README.Debian...
modifying debian/rules...
copying legacy postinstall template...
Copying source tree...
Gathering binaries...Marking modules for 3.0.0-12-generic (x86_64) for archiving...

Creating tarball structure to specifically accomodate binaries.

Tarball location: /var/lib/dkms/rr64x/1.0/tarball//rr64x-1.0.dkms.tar.gz


DKMS: mktarball Completed.

Copying DKMS tarball into DKMS tree...
Building binary package...dpkg-buildpackage: warning: using a gain-root-command while being root
 dpkg-source --before-build rr64x-dkms-1.0
 fakeroot debian/rules clean
make: dh_testdir: Command not found
make: *** [clean] Error 127
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
(bad exit status: 2)
Error! There was a problem creating your deb.

Everything works just fine but I can't create a DEB File which I kind of like in case I need to rebuild.

---

### Post by bvanaerde on 2011-11-15
Keep in mind that HighPoint will probably not be updating their drivers, even though it involves these simple changes.
I'm saying this, because I just received a reply from their helpdesk, when asking for up to date drivers for my RocketRaid1740:
> Dear Sir or Madam,

The card cannot support that new system kernel version.

Regards
Global Support Center
HighPoint Technologies, Inc.
Needless to say I'm not really happy with their support. I asked for updated drivers in 2009, and they never provided it either. I guess I will have to search for a different brand in the future.

---

### Post by bvanaerde on 2011-11-16
After an angry mail of mine, they replied with this:
> Dear Sir or Madam,

Actually we are mainly working on the new and high-level card.haven't got the time for updating on that model card.Sorry for the incovnenience.

Regards
Global Support Center
HighPoint Technologies, Inc.

---

### Post by 1of16 on 2011-11-18
thank you for your scripts, but i couldn't get it working:

```
DKMS make.log for rr231x-2.5 for kernel 3.0.0-12-generic (x86_64)
Fr 18. Nov 11:30:17 CET 2011
make: Gehe in Verzeichnis '/var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux'
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/os_linux.o
  CC [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/osm_linux.o
  CC [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/div64.o
  CC [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/hptinfo.o
  CC [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/config.o
  LD [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/rr2310_00.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/.him_rr2310pm.o.cmd for /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/him_rr2310pm.o
  CC      /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/rr2310_00.mod.o
  LD [M]  /var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux/.build/rr2310_00.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.0.0-12-generic'
make: Verlasse Verzeichnis '/var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux'
```any idea, what i may done wrong?

ok sry...now i noticed in post three, its already posted and just doesn't work with dkms.
got it working now manually....thank you very much!!!!

---

### Post by spschneer on 2011-11-25
> **krutoileshii said:**
> How I've gotten the RocketRaid 2640x4 driver to compile under 3.0 kernel.

Initially I've followed the steps outlined on the  [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid). However, it still failed to compile due to checks for the kernel version which required additional modifications to the Madefile.def located in the "inc" folder and install.sh files. Below I will outline the steps required to compile the driver.

[LIST=1]
[*]Dowload the open source driver form the HighPoint website (cur ver. 1.3) [http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz](http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz)
[*]Extract the driver to your home directory
[*]Open the Makefile.def located in the /inc/linux folder
[*] Replace the following:

This
```

KERNEL_VER := 2.$(shell expr `grep LINUX_VERSION_CODE $(KERNELDIR)/include/linux/version.h | cut -d\  -f3` / 256 % 256)

```
With 
```

KERNEL_VER := $(shell uname -r | cut -f1-2 -d.)

```

This
```

ifneq ($(KERNEL_VER), 2.6)

ifneq ($(KERNEL_VER), 2.4)

$(error Only kernel 2.4/2.6 is supported but you use $(KERNEL_VER))

endif

endif

```

With 

```

ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 3.0)
ifneq ($(KERNEL_VER), 2.4)
$(error Only kernel 2.4/2.6/3.0 is supported but you use $(KERNEL_VER))
endif
endif
endif

```

This

```

ifeq ($(KERNEL_VER), 2.6)

```

With 

```

ifeq ($(KERNEL_VER), $(filter $(KERNEL_VER),3.0 2.6))

```

Save the file.
[*] Open os_linux.h and remove the linux/config.h include statement
[*] Open os_linux.c file and change the follwing

From
```

blkdev_get(bdev, FMODE_READ)

```

To
```

blkdev_get(bdev, FMODE_READ, NULL)

```
Save.
[*] Open osm_linux.c and change the following:

From 

```

static int hpt_queuecommand (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *))

```

to 

```

static int hpt_queuecommand_lck (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *)) 

```

Before the hpt_reset method, insert the lines below:
```

#ifdef DEF_SCSI_QCMD
DEF_SCSI_QCMD(hpt_queuecommand)
#else
#define hpt_queuecommand hpt_queuecommand_lck
#endif

```
Save.

[*]Open install.sh and change section below from:
 
```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac

```

to 

```

case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
	3.0 )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac


```
[/LIST]

The driver should compile and install properly after that. 


I know that some of these things could be automated with a patch program, but i have no clue how to do it. if anyone is willing to tackle it, or help me write it, please send me an e-mail.


Hope this helps other people.
THANK YOU...I was able to use the info in your message (with a few tweaks) to get the driver for the HighPoint RocketRaid 622 to compile (and also work with dkms).  Here's what was different(for version 1.1 of the drivers from HighPoint's site)...   [http://www.highpoint-tech.cn/BIOS_Driver/rr62x/linux/rr62x-linux-src-v1.1-091221-1456.tar.gz](http://www.highpoint-tech.cn/BIOS_Driver/rr62x/linux/rr62x-linux-src-v1.1-091221-1456.tar.gz) 

[LIST]
[*]In Step 5.  my file name was **osm_linux.h**,
[*]I had to ensure **dkms** was installed (for the basic stuff for compiles/etc),
[*]I had to install **dpkg-dev** and **debhelper** to get mkdeb to work properly,
[*]Here's the dkms.conf file I used for the mkdeb (note the file names & version # were changed for the rr62x series card)
[/LIST]

```
MAKE="make -C product/rr62x/linux/ KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr62x/linux/ clean"
BUILT_MODULE_NAME=rr62x
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr62x/linux/
PACKAGE_NAME=rr62x
PACKAGE_VERSION=1.1
AUTOINSTALL=yes
REMAKE_INITRD=yes
```

As documented in the original How-TO...I did have to add the rr62x to the /etc/modules for boot load.

Thanks again and if "Despotism" is reading this, **Thank you** for your great HOW-TO.

---

### Post by Batman77 on 2012-03-24
When I Run sudo dkms build -m rr64x -v 1.0

I get this Error

[I]Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.0.0-16-generic -C product/rr64x/linux/ KERNELDIR=/lib/modules/3.0.0-16-generic/build....(bad exit status: 2)
Error! Bad return status for module build on kernel: 3.0.0-16-generic (x86_64)
Consult /var/lib/dkms/rr64x/1.0/build/make.log for more information.[/I]



**My make.log reads as follows**



DKMS make.log for rr64x-1.0 for kernel 3.0.0-16-generic (x86_64)
Sat Mar 24 18:29:34 SAST 2012
make: Entering directory `/var/lib/dkms/rr64x/1.0/build/product/rr64x/linux'
../../../inc/linux/Makefile.def:165: *** missing `endif'.  Stop.
make: Leaving directory `/var/lib/dkms/rr64x/1.0/build/product/rr64x/linux'

any ideas?

---

### Post by Batman77 on 2012-03-25
> **Batman77 said:**
> When I Run sudo dkms build -m rr64x -v 1.0

I get this Error

[I]Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.0.0-16-generic -C product/rr64x/linux/ KERNELDIR=/lib/modules/3.0.0-16-generic/build....(bad exit status: 2)
Error! Bad return status for module build on kernel: 3.0.0-16-generic (x86_64)
Consult /var/lib/dkms/rr64x/1.0/build/make.log for more information.[/I]



**My make.log reads as follows**



DKMS make.log for rr64x-1.0 for kernel 3.0.0-16-generic (x86_64)
Sat Mar 24 18:29:34 SAST 2012
make: Entering directory `/var/lib/dkms/rr64x/1.0/build/product/rr64x/linux'
../../../inc/linux/Makefile.def:165: *** missing `endif'.  Stop.
make: Leaving directory `/var/lib/dkms/rr64x/1.0/build/product/rr64x/linux'

any ideas?

All working now,, without DKMs

---

### Post by Dutchnutcase on 2012-04-27
Giving a small bump. I've made a patch for Ubuntu 12.04 (see attachment).

It can be applied with:
```
gunzip rr231x_0x-linux-src-v2.5-patch.diff.gz
patch -p1 < rr231x_0x-linux-src-v2.5-patch.diff
```in original rr23* directory.

---

### Post by buffalojr on 2012-05-16
Tweaked the files mentioned in the OP to include 3.2 and everything seems to work for rr64x series card as well.

---

### Post by MezzFA0 on 2012-08-05
For anyone battling with this, the newer 1.4 Linux drivers for the rr26xx cards work fine without tweaking.

[http://www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.4-120524-1520.tar.gz](http://www.highpoint-tech.com/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/rr264x-linux-src-v1.4-120524-1520.tar.gz)

All I did was install build-essential and the linux headers.  The normal make and sudo make install works fine.

I did add rr26xx to the /etc/modules file just in case.

---

### Post by edika32 on 2012-08-29
Have some problem with this one. I've downloaded v1.5 and compiled it without any changes and it goes trough. 

OUTPUT:
```

edika@newton:~/rr264x-linux-src-v1.5/product/rr2640/linux$ make 
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/os_linux.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/osm_linux.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/div64.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/hptinfo.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/config.o
  LD [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/rr26xx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/.him_odin.o.cmd for /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/him_odin.o
  CC      /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/rr26xx.mod.o
  LD [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/rr26xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
edika@newton:~/rr264x-linux-src-v1.5/product/rr2640/linux$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/os_linux.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/osm_linux.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/div64.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/hptinfo.o
  CC [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/config.o
  LD [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/rr26xx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/.him_odin.o.cmd for /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/him_odin.o
  LD [M]  /home/edika/rr264x-linux-src-v1.5/product/rr2640/linux/.build/rr26xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
You made a module which is for current kernel 3.2.0-29-generic.
Deleting previous installed driver module rr26xx...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
edika@newton:~/rr264x-linux-src-v1.5/product/rr2640/linux$  

```Updated my /etc/modules and added rr26xx and rebooted. 



Here is the output from ```
parted -l
``````

edika@newton:~$ sudo parted -l
Model: ATA ST3250410AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  242GB  242GB   primary   ext4
 2      242GB   250GB  8450MB  extended
 5      242GB   250GB  8450MB  logical   linux-swap(v1)


Error: /dev/sdc: unrecognised disk label                                  

Error: /dev/sdd: unrecognised disk label                                  



```

I've also tried to set a label on the disks without success output below
```
edika@newton:~$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/sdc                                                  
Using /dev/sdc
(parted) print                                                            
Error: /dev/sdc: unrecognised disk label                                  
(parted) mklabel msdos                                                    
Error: Invalid argument during seek for read on /dev/sdc                  
Retry/Ignore/Cancel?                                                      

```


And I've two disks installed on my card. What could be the problem ? 




Thanks

---

