---
title: "Not being able to install &quot;VMware Server 1.0.8 build-126538&quot; on Ubuntu 8.04"
date: 2008-11-28
forum: General Help
---

### Post by paragkalra on 2008-11-28
Hello folks,

 I installed Ubuntu 8.04 on my laptop. I then updated the Ubuntu packages before installing VMware. I don't remember my initial kernel version but my present kernel version is:

# uname -a
Linux station3 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
#

I then started the VMware server installation and problem started from here:

 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

[B]Your kernel was built with "gcc" version "4.2.3", while you are trying to use
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and
VMware Server may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "4.2.4" anyway? [no] yes[/B]

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-21-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
/tmp/vmware-config0/vmmon-only/common/vmx86.c: In function ‘Vmx86_GetkHzEstimate’:
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1899: warning: passing argument 4 of ‘Div643264’ from incompatible pointer type
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1908: warning: passing argument 4 of ‘Div643232’ from incompatible pointer type
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] yes

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, eth1.
Which one do you want to bridge to vmnet0? [eth0]

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no]

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] no

Do you want to be able to use host-only networking in your virtual machines?
[no]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902]

inetd: no process killed
Unable to make the Internet super-server (inetd) re-read its configuration
file.  Please restart inetd by hand:
killall -v -HUP inetd

Hit enter to continue.

Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Unable to compile the VMware VmPerl Scripting API.

********
The VMware VmPerl Scripting API was not installed.  Errors encountered during
compilation and installation of the module can be found here:
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program.

Errors can be found in the log file:
'/tmp/vmware-config0/control-only/make.log'
********

Hit enter to continue.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines] /data/virtual_machines

The path "/data/virtual_machines" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Do you want to enter a serial number now? (yes/no/help) [no] yes

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel: 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done

The configuration of VMware Server 1.0.8 build-126538 for Linux for this
running kernel completed successfully.

root@station3:/data/softwares/linux/vmware/vmware-server-distrib#

 

 

[B] So the problem is due to the fact that I have upgraded the gcc compiler. However when I am trying to remove gcc "4.2.4", It says it's dependent on gcc "4.2.3" and doesn't let me uninstall it. So I am left with only option uninstalling both or keeping them as it is.
[/B]
 Has anyone encountered this problem before?

---

