---
title: "Unichrome support in Ubuntu"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by Rinnan on 2005-03-30
Hello...

I've got a Unichrome video chipset (Mini-Itx VIA Nehemiah M10000 motherboard) and would like to see Unichrome support in Ubuntu.

Support exists in Linux (see this project : [http://unichrome.sourceforge.net](http://unichrome.sourceforge.net)) and works quite well, but you have to build it using the kernel sources (kernel headers are not enough) and I just can't get it to work.

In other distro's there usually a package, but I'd like to see it as an official part of the kernel package, so that upgrades are followed.

There is also an xorg driver that needs to be built (with the xorg sources).  

Has anyone done this manually who can help me out?  

I just get kernel panicks and "attempting to kill init!" whenever I try to install my own kernel (built with Ubuntu's config file), and another error (wrong magic number or something) if I try to load the module into the current kernel.  

Haven't even gotten to the xorg part.

Without this I can't make any real use of my video.

How do I proceed?

Erik

---

### Post by Paul Sinnett on 2005-03-31
[QUOTE=Rinnan]
I just get kernel panicks and "attempting to kill init!" whenever I try to install my own kernel (built with Ubuntu's config file), and another error (wrong magic number or something) if I try to load the module into the current kernel.  
[/QUOTE]

I also have a Unichrome card on an Acer 1362LC laptop. Having support for this would be cool but there's nothing I really need it for so I haven't bothered looking. I'll see if I can reproduce your problems when I next have some free time. What process are you following for compiling / patching / installing the new kernel under Hoary?

---

### Post by Rinnan on 2005-03-31
Actually I got much further this time.  I simply used [these instructions](http://www.ubuntulinux.org/wiki/KernelHowto) to build a kernel, then used my own little script to fetch, build, and install the DRM module from CVS.  Here's the script:

```
#!/bin/bash

DRMDATE="2004-11-05"
KERNELVER="2.6.10.viafix"

cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri login
cvs -z3 -d:pserver:anonymous@dri.freedesktop.org:/cvs/dri co -D $DRMDATE drm
cd drm/linux-2.6; make DRM_MODULES="via"
cp via.ko /lib/modules/$KERNELVER/kernel/drivers/char/drm/via.ko
```

Change "KERNELVER" to whatever you called your kernel in the kernel building step.  This brought me about 1/3 of the way, now there's DRM support in the kernel.  I still need to build the xorg driver, so I need the source to the specific xorg that is being used in Ubuntu, then from that I'll build another cvs getting, building, and installing script for that.

NOTES:  
#1:  Use "viafix" for the --append-to-version while building the kernel.
#2:  Change the "Processor Type" in the kernel config to anything other than 386 -- 386 won't work and that's the default used by Ubuntu.  If you are actually running on a 386 (as opposed to 486, pentium, p3, p4, athlon or anything but a real 386) you are out of luck.  I don't imagine that Ubuntu would run on a 386 anyway!
#3:  The script will leave a "drm" directory in whatever directory it's run in.  You can delete it when you are done if you want.

Erik

---

### Post by dwmcqueen on 2005-04-11
Have you had any progress in this?  

I noticed my Unichrome in the auto-default tries to load the S3 driver, but looks bad.  I'd like to run in something other than the Vesa driver  ;-) .

---

### Post by Paul Sinnett on 2005-04-13
[QUOTE=dwmcqueen]Have you had any progress in this?  
[/QUOTE]

I just saw that VIA have open sourced their linux drivers which is great news. It shouldn't be long before these drivers get packaged up for Ubuntu. We'll probably have drivers detected and installed by default by the time Breezy comes along. :-)

---

### Post by magicfab on 2005-04-13
In other news, [VIA Releases Linux Driver Source Packages](http://www.via.com.tw/en/resources/pressroom/2005_archive/pr050412_driversource.jsp) .

There's an interesting [discussion](http://linuxdevices.com/cgi-bin/board/UltraBoard.pl?Action=ShowPost&Board=talkbacks&Post=394) at [LinuxDevices.com](http://linuxdevices.com/news/NS5778694249.html)

---

### Post by Rinnan on 2005-04-14
[QUOTE=Paul Sinnett]I just saw that VIA have open sourced their linux drivers which is great news. It shouldn't be long before these drivers get packaged up for Ubuntu. We'll probably have drivers detected and installed by default by the time Breezy comes along. :-)[/QUOTE]
 Yeah I read the release annoucement as well, and am really looking for out-of-the-box support.  The driver does work (without using VESA) on my Nehemiah M10000, so are you sure there's not some other configuration problem?  It worked out-of-the-box as far as 2D.

---

### Post by Rinnan on 2005-04-14
[QUOTE=dwmcqueen]Have you had any progress in this?  

I noticed my Unichrome in the auto-default tries to load the S3 driver, but looks bad.  I'd like to run in something other than the Vesa driver  ;-) .[/QUOTE]
 It seems to work right out of the box for me (Nehemiah M10000) in 2D without VESA.

What chipset are you using?

---

### Post by fede on 2005-04-18
Hello Rinnan,

   I was trying to follow the instrucions you pointed to in your post. But I'm a newbie, and figuring out the options in the make xconfig step seems quite scary at this time, and in any case I guess that by the time I'd figure it out I'd probably be running Breezy with proper via unichrome support... (or so I hope, at least).
   I tried what happened if I accepted the "default" options (since make xconfig said something about importing the defaults from my current kernel, which seems to work allright,  2.6.10.5-k7). But it didn't compile...
    So seeing your post I was wondering, perhaps using your options file would work fine for me too? Do you think it might, and if so could you please post this file?

Thanks!

PD: I'm running an ASUS A7400-MX with via KM400A chipset. I've been browsing around and still I don't understand why it is necessary to compile a custom kernel to include the unichrome driver (a measure of my ignorance).

---

### Post by NaplesBill on 2005-04-19
I just replaced my mb and CPU with a MicroATX MB/AMD Sampron 2200+ combo.  The board has an S3 Unichrome VIA chipset.  This is my second PC so I'm more than happy with the performance.  I installed ubuntu from the download CD and it worked perfectly.  The driver in xorg.conf is "via" so the support seems to be in Ubuntu 5.04 already.

---

### Post by k4p0w3r on 2005-04-20
I'm using Via EPIA M10000 with the Castlerock (CLE266) chipset and Ubuntu 5.04 detected it right away and xorg is happily using the via driver. 
All work fine except DRI. glxgears show around 90 fps. DRI is not loaded according to glxinfo and /var/log/Xorg.0.log:

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via"
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.

xorg.conf has got all the correct settings as far as I can see (including the DRI tag at the bottom of the file). There is no via_dri.o in the modules for X though and even if I add the binary manually it will not load.
There are workarounds according to [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) but they are specific to distros. Even Debian has got a solution but not for xorg it seems.
It would be sweet to get DRI support for CLE266. I just can't get enough of armagetron  :-P 

To all Ubuntu coders: Thanks for a top notch distro (and consider my request)

---

### Post by ldoria on 2005-06-01
Hi guys,

I'm just a newbie at linux and I use Hoary but I can't make ragnarok works on ubuntu.
I use a via s3 unichrome and I've downloaded some packages from debian to install, because I can't find the right drive at synaptic.
So I got xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb, drm-trunk-module-src_2005.02.08-1_all, xserver-xfree86-dri-trunk_2005.02.08-1_i386 but I couldn't install through dpkg. I always have the same error.

luciana@Garfield:~/Desktop$ sudo dpkg -i xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb
(Lendo banco de dados ... 71439 arquivos e diretórios atualmente instalados.)
Descompactando xlibmesa-gl1-dri-trunk (de xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb) ...
Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so.1.0 to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so.1.0 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so.1 to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/libGL-no-dri-trunk.so.1.2 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/libGL-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/libGL-no-dri-trunk.so.1.2 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/lib/libGL.so.1 to /usr/lib/libGL-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'
dpkg: erro processando xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb (--install):
tentando sobrescrever `/usr/X11R6/bin/xdriinfo', que também está no pacote xbase-clients
Erros foram encontrados durante processamento de:
xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb

someone has any idea how to install this package?

Tks a lot.

---

