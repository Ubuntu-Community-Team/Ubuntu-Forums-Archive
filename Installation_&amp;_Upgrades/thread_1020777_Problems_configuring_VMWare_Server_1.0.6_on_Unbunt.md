---
title: "Problems configuring VMWare Server 1.0.6 on Unbuntu 8.10"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by antimac on 2008-12-24
I was able to install VMWare Server 1.0.6-918891 on Unbuntu 8.10 with kernel 2.6.27-27-generic, when I run either ./vmware-config.pl or ./runme.pl from the vmware-update-2.6.27-5.5.7-2 I get the following error:

root@myra-desktop:/home/myra/Desktop/vmware-update-2.6.27-5.5.7-2# ./runme.pl 

Updating /usr/bin/vmware-config.pl ... already patched 
Updating /usr/bin/vmware ... No patch needed/available 
Updating /usr/bin/vmnet-bridge ... No patch needed/available 
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available 
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available 
VMware modules in "/usr/lib/vmware/modules/source" has been updated. 


Before running VMware for the first time after update, you need to configure it 

for your running kernel by invoking the following command: 

"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped. 

Stopping VMware services: 

Virtual machine monitor done 

Configuring fallback GTK+ 2.4 libraries. 

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 


/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path 

/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path 

Trying to find a suitable vmmon module for your running kernel. 

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel. Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 
Using compiler "/usr/bin/gcc". Use environment variable CC to override. 


What is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module. 

Building the vmmon module. 


Building for VMware Server 1.0.0. 
Using 2.6.x kernel build system. 
make: Entering directory `/tmp/vmware-config3/vmmon-only' 
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic' 
CC [M] /tmp/vmware-config3/vmmon-only/linux/driver.o 
CC [M] /tmp/vmware-config3/vmmon-only/linux/driverLog.o 
CC [M] /tmp/vmware-config3/vmmon-only/linux/hostif.o 
/tmp/vmware-config3/vmmon-only/linux/hostif.c: In function ‘HostIF_SetFastClockRate’: 
/tmp/vmware-config3/vmmon-only/linux/hostif.c:3441: warning: passing argument 2 of ‘send_sig’ discards qualifiers from pointer target type 
CC [M] /tmp/vmware-config3/vmmon-only/common/comport.o 
CC [M] /tmp/vmware-config3/vmmon-only/common/cpuid.o 
CC [M] /tmp/vmware-config3/vmmon-only/common/hash.o 
CC [M] /tmp/vmware-config3/vmmon-only/common/memtrack.o 
CC [M] /tmp/vmware-config3/vmmon-only/common/phystrack.o 
CC [M] /tmp/vmware-config3/vmmon-only/common/task.o 
gcc: error trying to exec 'cc1plus': execvp: No such file or directory 
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/task.o] Error 1 
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
make: *** [vmmon.ko] Error 2 
make: Leaving directory `/tmp/vmware-config3/vmmon-only' 
Unable to build the vmmon module. 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html". 
Execution aborted. 


root@myra-desktop:/home/myra/Desktop/vmware-update-2.6.27-5.5.7-2# 


Does anybody have any ideas? Thanks.

---

### Post by Partyboi2 on 2008-12-24
Have you got build-essential package installed? In a terminal (Applications>Accessories>Terminal)
```
sudo apt-get install build-essential
```

---

### Post by antimac on 2008-12-30
worked like a charm. What is build-essential?

---

### Post by Partyboi2 on 2009-01-01
Build-essential is a meta package that installs packages used for compiling.
     
   > If you do not plan to build Debian packages, you don't need this package.  Starting with dpkg (>= 1.14.18) this package is required for building Debian packages. 
 This package contains an informational list of packages which are considered essential for building Debian packages.  This package also depends on the packages on that list, to make it easy to have the build-essential packages installed. 
 If you have this package installed, you only need to install whatever a package specifies as its build-time dependencies to build the package.  Conversely, if you are determining what your package needs to build-depend on, you can always leave out the packages this package depends on. 
 This package is NOT the definition of what packages are build-essential; the real definition is in the Debian Policy Manual. This package contains merely an informational list, which is all most people need.   However, if this package and the manual disagree, the manual is correct
. 	  
                        [B]
[/B]

---

