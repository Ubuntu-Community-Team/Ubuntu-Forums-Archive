---
title: "Logitech Quickcam Messenger: 2.6.20-9-generic/build missing"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by KIAaze on 2007-05-14
I am trying to install the driver for my Logitech Quickcam Messenger webcam.
I downloaded the driver here:
[http://home.mag.cx/messenger/]("http://home.mag.cx/messenger/")

However, when I execute ./quickcam.sh, I get this error message:

> awk: cannot open /lib/modules/2.6.20-9-generic/build/include/linux/version.h (No such file or directory)
[: 1: 132608: unexpected operator
[: 1: 132608: unexpected operator
Kernel source directory: /lib/modules/2.6.20-9-generic/build
[!] Can not find kernel source or even headers.
Make sure that they are installed (install with e.g. rpm or apt-get
if necessary) and ensure that you have read rights to the files.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->    

Here's what's in my /lib/modules:
```
>ls /lib/modules/*/
/lib/modules/2.6.17-10-generic/:
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  volatile
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap

/lib/modules/2.6.17-11-generic/:
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  volatile
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap

/lib/modules/2.6.20-13-generic/:
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  volatile
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap

/lib/modules/2.6.20-15-generic/:
build   kernel   modules.alias   modules.dep          modules.inputmap   modules.ofmap   modules.seriomap  modules.usbmap
initrd  madwifi  modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap  modules.symbols   volatile

/lib/modules/2.6.20-6-generic/:
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  volatile
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap

/lib/modules/2.6.20-8-generic/:
build   kernel   modules.alias   modules.dep          modules.inputmap   modules.ofmap   modules.seriomap  modules.usbmap
initrd  madwifi  modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap  modules.symbols   volatile

/lib/modules/2.6.20-9-generic/:
initrd  madwifi        modules.ccwmap  modules.ieee1394map  modules.isapnpmap  modules.pcimap    modules.symbols  volatile
kernel  modules.alias  modules.dep     modules.inputmap     modules.ofmap      modules.seriomap  modules.usbmap

/lib/modules/2.6.22-1-generic/:
build

```

Why does the script look in 2.6.20-9-generic and why is there no build directory in it?
What should I do to get this build directory?

Here's the complete output so far:```

>./quickcam.sh
-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: gcc version 4.1.3 20070429 (prerelease) (Ubuntu 4.1.2-5ubuntu3)
gcc version: gcc version 4.1.3 20070429 (prerelease) (Ubuntu 4.1.2-5ubuntu3)
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.17.50.20070426
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu3)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.3-pre2
insmod version: module-init-tools version 3.3-pre2
rmmod version: module-init-tools version 3.3-pre2
modprobe version: module-init-tools version 3.3-pre2
Checking whether we're root... kiaaze
Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

awk: cannot open /lib/modules/2.6.20-9-generic/build/include/linux/version.h (No such file or directory)
[: 1: 132608: unexpected operator
[: 1: 132608: unexpected operator
Kernel source directory: /lib/modules/2.6.20-9-generic/build
[!] Can not find kernel source or even headers.
Make sure that they are installed (install with e.g. rpm or apt-get
if necessary) and ensure that you have read rights to the files.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->               
```

I passed the part about the kernel compiler supposing it wouldn't cause any problems.

OS: Ubuntu Gutsy Gibbon

---

