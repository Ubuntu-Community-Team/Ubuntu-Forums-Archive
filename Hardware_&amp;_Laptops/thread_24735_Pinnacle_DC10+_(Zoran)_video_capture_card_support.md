---
title: "Pinnacle DC10+ (Zoran) video capture card support?"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by fsman on 2005-04-08
Is the Pinnancle DC10+ (Zoran chipset) based card working in Hoary? I know that the live CD shows in the the device manager but don't know if the zoran kernal module is included in Hoary.

Has anyone got this card working and if so how?

many thanks in advance

---

### Post by Canguçu on 2005-04-08
Try typing "sudo modprobe zr36067" in the terminal.

I have that same card. I'm still installing Hoary here, when I get my card to work I'll tell you how.

Oh, and visit [http://mjpeg.sourceforge.net/driver-zoran/](http://mjpeg.sourceforge.net/driver-zoran/)

---

### Post by fsman on 2005-04-08
modprode didn't work, i got the following

modprobe zr36067
FATAL: Module zr36067 not found.

any ideas?

---

### Post by seb/vdn on 2005-04-13
[QUOTE=fsman]Is the Pinnancle DC10+ (Zoran chipset) based card working in Hoary? I know that the live CD shows in the the device manager but don't know if the zoran kernal module is included in Hoary.

Has anyone got this card working and if so how?

many thanks in advance[/QUOTE]
 hi ,

i have the same problems ! but i'm trying to make a new kernel with the source of the kernel 2.6.11 . and finally when i type modprobe zr36067 ,the module was loaded .But (another But !) when i start Xawtv,i have a black screen and xawtv said : v4l-conf was not compiled with dga support ! anyone have a idea ? or how to compil xawtv and v4l-conf with dga support ?
thanks.
seb.

---

### Post by x2l2 on 2005-04-16
same problem here :(

i try to build a new kernel but got a error went i run lilo

 Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hdc1'

i going to wait for seb/vdn kernel (make-kpkg and give this deb file to all :P) 
did you try disable dga ? 
[shell]# xawtv -debug 2 -noxv -noscale -novm -nodga
                                                                       ^^^^^

when i search for dga only found a lot of docs about disable dga o Xf86config  ](*,)

---

### Post by seb/vdn on 2005-04-17
[QUOTE=x2l2]same problem here :(

i try to build a new kernel but got a error went i run lilo

 Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hdc1'

i going to wait for seb/vdn kernel (make-kpkg and give this deb file to all :P) 
did you try disable dga ? 
[shell]# xawtv -debug 2 -noxv -noscale -novm -nodga
                                                                       ^^^^^

when i search for dga only found a lot of docs about disable dga o Xf86config  ](*,)[/QUOTE]
 to x2l2 : for build a new kernel,i used this how to : [http://www.trustonme.net/didactels/285.html](http://www.trustonme.net/didactels/285.html)

and finally,about my black screen with xawtv,no dga support ,i think the problems must be come from my video cards : a radeon 9200 .perhaps,i'm not sure .
so,at this time time,my dc 10 device don't work with xawtv or with the mjpegtools.

---

### Post by fsman on 2005-04-17
[QUOTE=seb/vdn]to x2l2 : for build a new kernel,i used this how to : [http://www.trustonme.net/didactels/285.html](http://www.trustonme.net/didactels/285.html)

and finally,about my black screen with xawtv,no dga support ,i think the problems must be come from my video cards : a radeon 9200 .perhaps,i'm not sure .
so,at this time time,my dc 10 device don't work with xawtv or with the mjpegtools.[/QUOTE]
 I can't seem to rebuild my kernel to include zoran on 2.6.10.
I run  make menuconfig and I tried to include Zoran and then the submodule DC10+
However, my rebuilt kernel gives me a kernel panic on reboot.
Have I done something wrong? Should I have included all of the submodules under the Zoran  module

---

### Post by x2l2 on 2005-04-18
seb/vdn , i have a radeon 9250 card i just try a knoppix cd (exactly knoppix 3.6 old cd) an d modprobe the modules (saa7110 and zr36037) and it works!  \\:D/  try knoppix  live cd

i use 
[http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)
and have a kernel panic too , i try again later at this way

[http://www.ubuntulinux.org/wiki/KernelBuildpackageHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageHowto)

sorry for my bad english

---

### Post by seb/vdn on 2005-04-19
hi to all ! 

it work on ubuntu !

My english was very bad ! if someone speak french and english fine to write a how to,i'm very pleased to explain how i dit it !

But i'm trying to explain : 

i make a new kernel with the source 2.6.8 ,i'm inclued the support for the zoran chipset .When i make my new kernel,in the bash i type modprobe zr36067 .

i'm go to find the last rpm from xawtv for fedora core 3 (because i like this other distrib !) with the aliens command i make a deb,i'm install it on my computer (dpkg -i xawtv3.94.deb) ,and i launch xawtv,and what i see ? my video ! no black screen ! 
i'm testing the lavrec command,it work too !

so bye !
seb .

---

### Post by Marco Carvalho on 2005-04-19
I don't understand why Ubuntu kernel is compiled without Zoran modules. All Debian 2.6 kernel-images came with zoran modules.

from config-2.6.10-5-k7:

# CONFIG_VIDEO_ZORAN is not set
# CONFIG_VIDEO_ZR36120 is not set

 ](*,) 

P.S. My English is terrible, sorry.

UPDATE:

Have an entry in Bugzilla about this:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8817](https://bugzilla.ubuntu.com/show_bug.cgi?id=8817)

Bugzilla Bug 8817
	  	Zoran video driver not configured in kernel
 Status:   	PENDINGUPLOAD
 Target Milestone:     Ubuntu 5.10

---

### Post by x2l2 on 2005-04-23
i instaled debian kernel-image 
[http://packages.debian.org/unstable/base/kernel-image-2.6.10-1-686](http://packages.debian.org/unstable/base/kernel-image-2.6.10-1-686)
and xawtv rpm 

but looks very slow :( 
in knoppix goes to a normal speed 

sorry for my english again >_<

---

### Post by fsman on 2005-04-23
[QUOTE=seb/vdn]hi to all ! 

it work on ubuntu !

My english was very bad ! if someone speak french and english fine to write a how to,i'm very pleased to explain how i dit it !

But i'm trying to explain : 

i make a new kernel with the source 2.6.8 ,i'm inclued the support for the zoran chipset .When i make my new kernel,in the bash i type modprobe zr36067 .

i'm testing the lavrec command,it work too !

so bye !
seb .[/QUOTE]

Can you list step by step how you rebuilt your kernel and installed to get Zoran working - I still get kenel panics.

Thanks

---

