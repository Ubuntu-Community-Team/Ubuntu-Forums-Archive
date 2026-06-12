---
title: "Problem on installinh VMware 5.5"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by noeluylee on 2005-12-28
I install vmware and it worked perfectly, I un-install it for some reason. Now I tried to install it again following the instruction located at [http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware)  now I encounter an error.

right after the location of the directory of C header:

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and VMware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.12-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
[I]cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++[/I]
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

Extracting the sources of the vmnet module.

Building the vmnet module.

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and V Mware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.12-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/.modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

Execution aborted.

Hope you guys can help me as Im keen to fix this problem.

Regards and Thanks, Noel

---

### Post by noeluylee on 2005-12-28
help? :-(

---

### Post by anil_robo on 2005-12-28
1. I'm not an expert by any means, but I'll suggest you check your version of gcc. If possible, please read the instructions at vmware website (use their search engine - they don't have a link to help page)
2. I really appreciate that you asked for help - all of us are here to help you. Unfortunately my technical expertise is limited, so I'd strongly suggest you use the search engine at ubuntu forums. I did a few searches for you, please try them:
[http://www.ubuntuforums.org/showthread.php?t=107063#2]("http://www.ubuntuforums.org/showthread.php?t=107063#2")
[http://www.ubuntuforums.org/showthread.php?t=76175](http://www.ubuntuforums.org/showthread.php?t=76175)

---

