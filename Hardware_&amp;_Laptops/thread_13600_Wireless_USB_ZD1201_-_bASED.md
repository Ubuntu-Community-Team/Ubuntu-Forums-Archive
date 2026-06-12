---
title: "Wireless USB ZD1201 - bASED"
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by epid on 2005-02-01
On Sourceforge at [http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/) a driver for ZD1201 USB wireless  key is found.

The driver package includes make systems to build the new driver, but 
UBUNTU says:

[email]root@......zd[/email]1201-0.13 # make
makefile:18: *** Kernel version 2.6.8 not supported by this driver..  Stop.
[email]root@..........zd[/email]1201-0.13 #

The accompanying readme file says:
Go into your kernel source directory (e.g. /usr/src/linux-2.6.7/) and execute
the following command: 	patch -p1 <zd1201-0.7/2.6.7-usb-broken-descriptor.diff

It is wise to do a dry run first:	patch -p1 --dry-run <zd1201-0.7/2.6.7-usb-broken-descriptor.diff
This way you can try each of the different patches first to see which version you need.

Now rebuild your kernel and install it or if you have the usb subsystem as modules rebuild the modules and install them.
Recent 2.6.10-rc kernels should work with this device without patching.

Question: 
1. Is there a general patch for Ubuntu to go from 2.6.8 to 2.6.10 which would make not have to do the "patch" which I as a newcomer do not feel comfortable with. 

2. IF it is OK to do the patching where do I find the kernel source directory and how do I rebuild it after patching ? 
I saw no package to install it and apparently it is not installed with standard installation.

---

### Post by philcolbourn on 2005-05-06
I got it going after a little trouble.

make sure you install the latest 2.6.10 kernel.

1. You need to install the linux-source tree. the header package is missing a header file.
2. to do it without patching, 2.6.10 should work. it apparently has extra bits in the usb code to detect the zd1201 device (and others too).
3. After building it, I needed to move the file manually into the /lib/modules/<kernel version> directory. I am sure this is not the best way but it worked for me.

---

### Post by shrekbar on 2005-06-23
Hi Fhil

One question to near problem.

My kernel is a 2.6.10-5-k7
I'am installed the kernel-header to k7 and source-code kernel
the version driver is 0.14 zd1201
but make complains...

[PHP]/home/berta/Desktop/zd1201-0.14/zd1201.c:24:24: ieee802_11.h: El fitxer o directori no existeix
/home/berta/Desktop/zd1201-0.14/zd1201.c: En la funció "zd1201_usbrx":
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: `IEEE802_11_SCTL_FRAG' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: (Each undeclared identifier is reported only once
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: for each function it appears in.)
/home/berta/Desktop/zd1201-0.14/zd1201.c:332: error: `IEEE802_11_FCTL_MOREFRAGS' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:344: error: `IEEE802_11_DATA_LEN' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:349: error: `IEEE802_11_SCTL_SEQ' undeclared (first use in this function)
make[2]: *** [/home/berta/Desktop/zd1201-0.14/zd1201.o] Error 1
make[1]: *** [_module_/home/berta/Desktop/zd1201-0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
make: *** [modules] Error 2
[/PHP] 

is the ieee802_11.h my problem,the header package is missing a header file.Where is this module?

Can help me with this? please
I am confused
that it is what I make bad?
thanks

---

### Post by philcolbourn on 2005-06-23
[QUOTE=shrekbar]Hi Fhil

One question to near problem.

My kernel is a 2.6.10-5-k7
I'am installed the kernel-header to k7 and source-code kernel
the version driver is 0.14 zd1201
but make complains...

[PHP]/home/berta/Desktop/zd1201-0.14/zd1201.c:24:24: ieee802_11.h: El fitxer o directori no existeix
/home/berta/Desktop/zd1201-0.14/zd1201.c: En la funció "zd1201_usbrx":
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: `IEEE802_11_SCTL_FRAG' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: (Each undeclared identifier is reported only once
/home/berta/Desktop/zd1201-0.14/zd1201.c:331: error: for each function it appears in.)
/home/berta/Desktop/zd1201-0.14/zd1201.c:332: error: `IEEE802_11_FCTL_MOREFRAGS' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:344: error: `IEEE802_11_DATA_LEN' undeclared (first use in this function)
/home/berta/Desktop/zd1201-0.14/zd1201.c:349: error: `IEEE802_11_SCTL_SEQ' undeclared (first use in this function)
make[2]: *** [/home/berta/Desktop/zd1201-0.14/zd1201.o] Error 1
make[1]: *** [_module_/home/berta/Desktop/zd1201-0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
make: *** [modules] Error 2
[/PHP] 

is the ieee802_11.h my problem,the header package is missing a header file.Where is this module?

Can help me with this? please
I am confused
that it is what I make bad?
thanks[/QUOTE]
 it looks like you need the missing header file. install the kernel source package instead of the kernel header package and change the /usr/src/linux symlink.

or, if you can find the header file somewhere, add it to you kernel headers somewhere

---

### Post by philcolbourn on 2005-06-23
[QUOTE=philcolbourn]it looks like you need the missing header file. install the kernel source package instead of the kernel header package and change the /usr/src/linux symlink.

or, if you can find the header file somewhere, add it to you kernel headers somewhere[/QUOTE]
 oops, i didn't read your post correctly. you already have the source files installed so just change the /usr/src/linux symlink.

also, 'locate ieee802_11' you should see the the file is in the /usr/src/linux directory.

---

### Post by shrekbar on 2005-06-23
Thank Phil

it will make the changes
before probe,checkinstall create a debian Packages but I do not work
east weekend will try
thanks for your aid, I say some thing to you
I have two computers with the same problem , Ibook G3 900 , PC Sempron 2900 (the error is the same one)
UBUNTU hoary 5.04

 :)

---

### Post by shrekbar on 2005-06-28
Hi Phil

Sorry by not to have been able to have informed into as it were.

The PC same problem, the ieee802_11 is mising, it does not find any reference.

The Ibook, today update the powerPc-kernel 2.6.10-7, and the restricted modules.

but make complains...

[PHP]make
make -C /lib/modules/`uname -r`/build/ M=/home/pere/Desktop/zd1201 modules
make: *** /lib/modules/2.6.10-5-powerpc/build/: El fitxer o directori no existeix.  Stop.
make: *** [modules] Error 2
[/PHP] 
but these modules exist in the system.
it will investigate on the error of ibook
thanks for your support, I say some thing to you.

Sorry for my googlean english

---

### Post by biodiesel-bri on 2005-07-01
I've been struggling with this issue myself.  The 802_11.h file was removed from the Linux kernel source sometime in 2004 in a big purge of files not considered essential to the kernel.  Unfortunately, this broke a few drivers, including the zd1201.

Here's what I've done so far.  I'm sure there's a better way:

Download the 802_11.h file here:
[http://gsu.linux.org.tr/~mpekmezci/kernelapi/unitedlinux/drivers/net/wireless/ieee802_11.h.html](http://gsu.linux.org.tr/~mpekmezci/kernelapi/unitedlinux/drivers/net/wireless/ieee802_11.h.html)

Just in case that link goes dead I've attached the file to this message.  I had a hell of a time finding it.

I copied the ieee802_11.h to the directory where I had put the zd1201.c and the associated makefile.  I edited zd1201.c, about 15 lines in to read "ieee802_11.h" (include the quotes).  It originally read <ieee802_11.h> or something like that.

With that I was able to compile the driver.  Hooray.

I then copied the driver to /lib/modules/`uname -r`/drivers/net/wireless

Now I'm stuck -- dmesg reports that the firmware update fails -- asking for a hotplug firmware loader.  Any ideas how I might get that working?

-B

---

### Post by shrekbar on 2005-07-03
hi biodiesel

Thanks for your solution, i'm sorry to respond very late your post, I have been outside my home for familiars reasons.
it will prove it and tomorrow I say something to you.

thanks

see you

Pere

---

