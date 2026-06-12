---
title: "NEW ATI drivers tutorial"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by krak on 2005-09-17
Hello,
at the beggining i want to thank's people who have wrote tutorials links below.
[http://www.ubuntuforums.org/showthread.php?t=65276](http://www.ubuntuforums.org/showthread.php?t=65276)
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)
[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)
I have tried those tutorials non of them did work for me :) probably i have done something wrong i use linux for a mont. But what I have done, I have mixed those tutorials to make my drivers work and they do work.
This tutorial is for people which run default kernel in my case on Horay is 2.6.10-5-386. If you have custom kernel then just download ATI driver from ati.com
ati-driver-installer-8.16.20-i386.run and do
```

su
bash ati-driver-installer-8.16.20-i386.run

```
then Instal Driver 8.16.20 on X.Org 6.8.x.
After installing driver just run fglrxconfig and thats all did work for me! on kernel 2.6.13.1

But if you dont want go throught compilation of new kernel just download from ati.com this driver ati-driver-installer-8.16.20-i386.run then:
```

su
apt-get install fakeroot

xhost +
apt-get install build-essential
apt-get install linux-headers-$(uname -r)

``` 
after downloading linux-headers
You have to make deb packages for Ubuntu,
```

su
bash ati-driver-installer-8.16.20-i386.run

```
choose "Generate Distribution Specific Driver Package"
choose what ubuntu do you use and generate packs

installing drivers
```

dpkg -i xorg-driver-fglrx_8.16.20-1_i386.deb
dpkg -i fglrx-kernel-source_8.16.20-1_i386.deb
dpkg -i fglrx-control_8.16.20-1_i386.deb (optional)

```
after installing drivers do
```

cd /usr/src
bzcat fglrx.tar.bz2 | tar x

```
```

cd /usr/src/modules/fglrx
bash make.sh

```
```

mkdir /lib/modules/$(uname -r)/misc
cp fglrx.ko /lib/modules/$(uname -r)/misc/
depmod -ae

```
```

modprobe fglrx

```
now u have to generate xorg.conf file go [http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/)
after u have generated xorg.conf
```

cp /etc/X11/xorg.conf /etc/X11/xorg.bak
cd /etc/X11/
rm xorg.conf
nano xorg.conf

``` 
and copy and paste xorg.conf which u have generated at [http://www.objorkum.com/scripts/fglrconfig/](http://www.objorkum.com/scripts/fglrconfig/)
save you new xorg.conf
reset PC or X
to check drivers working or not type
```

fglrxinfo

``` 
you should get something like this
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

---

### Post by bagofchickens on 2005-09-17
Really helpful, thanks a bunch krak. 

Although, the 

cd /usr/src/modules/fglrx
bash make.sh

part was a bit tricky because in my case there was no /usr/src/modules/fglrx (there was a /usr/src/fglrx.tar.bz2 file which had to be uncompressed first)

---

### Post by krak on 2005-09-17
THANKS
oh yes i have missed 
cd /usr/src
bzcat fglrx.tar.bz2 | tar x
I have updated tutorial thx to "bagofchickens"

---

### Post by razoe on 2005-09-17
okay, I've downloaded the .run file, and whenever I run generate distribution... packages I select hoary and 5.04... but when It's finished I can't seem to find any drivers in the folder where the .run file is located ( home folder)
I sure do hope someone can help me out here  O:)

---

### Post by lucaspr on 2005-09-17
/tmp/fglrx <- they should be here!

That's where I found them :)

There's a little mistake in the tutorial too... The second link to the script site doesn't work. But that's, I believe a missing x...

Got the driver too work after all! Thanx A LOT for this howto!!! (should be in the unofficel ubuntu starters guide I think..... :))

---

### Post by krak on 2005-09-17
razoe u need to install fakeroot before creating ubuntu packages
for me it generated packages at my home folder
lucaspr i am happy i could help  \\:D/

---

### Post by Tylo on 2005-09-17
Nice Tutorial. I had absolutely no problems. Wish getting sound to work correctly was this easy.  :-P

---

### Post by Benzima on 2005-09-17
Wow !!! This worked for me. How cool. I've been trying every tutorial here, without success. I'm sure probably something I messed up, but this one worked.

Two things tripped me up. I didn't know how to save the xorg.conf while in nano. I beleive it's 'Ctrl C' to bring up the save window and then 'Ctrl X' to exit or something.

The other thing is now I one have 3 choices for resoultion. I've have to figure out how to change that. I think I can just go back into xorg.conf and add some.

Thanxxx again. 

Now, if I can just get my Logitech MX 1000 and Audigy 2 going, it will be goodbye Windows forever!!

---

### Post by ZarathustraDK on 2006-01-14
Argh! I'm almost there, but while I do make.sh I get :

> ==============================
root@ubuntu:/usr/src/modules/fglrx# sudo bash make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make.sh: line 849: cd: 2.6.x: Ingen sådan fil eller filkatalog
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /usr/src/modules/fglrx/agp3.o
  CC [M]  /usr/src/modules/fglrx/nvidia-agp.o
  CC [M]  /usr/src/modules/fglrx/agpgart_be.o
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_init':
/usr/src/modules/fglrx/agpgart_be.c:8173: advarsel: 'pm_register' er forældet (erklæret ved include/linux/pm.h:106)
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_cleanup':
/usr/src/modules/fglrx/agpgart_be.c:8183: advarsel: 'pm_unregister_all' er forældet (erklæret ved include/linux/pm.h:116)
/usr/src/modules/fglrx/agpgart_be.c: At top level:
/usr/src/modules/fglrx/agpgart_be.c:6077: advarsel: 'ati_gart_base' defineret, men aldrig brugt
  CC [M]  /usr/src/modules/fglrx/i7505-agp.o
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_putminor':
/usr/src/modules/fglrx/firegl_public.c:558: advarsel: 'inter_module_put' er forældet (erklæret ved include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c:560: advarsel: 'inter_module_unregister' er forældet (erklæret ved include/linux/module.h:565)
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_register':
/usr/src/modules/fglrx/firegl_public.c:580: advarsel: 'inter_module_register' er forældet (erklæret ved include/linux/module.h:564)
/usr/src/modules/fglrx/firegl_public.c:611: advarsel: 'inter_module_put' er forældet (erklæret ved include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:3492: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3493: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3494: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3495: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3496: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3497: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3498: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3499: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3501: advarsel: klargøring fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c:3511: advarsel: funktionserklæringen er ikke en prototype
/usr/src/modules/fglrx/firegl_public.c: In function `test_inter_module_interface':
/usr/src/modules/fglrx/firegl_public.c:3577: advarsel: 'inter_module_put' er forældet (erklæret ved include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c:3583: advarsel: 'inter_module_put' er forældet (erklæret ved include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c: In function `__ke_agp_allocate_memory_phys_list':
/usr/src/modules/fglrx/firegl_public.c:3841: advarsel: videregiver den 3. parameter af henvisning til funktion opretter et heltal ud fra en henvisningsvariabel uden en typeomtvingning
/usr/src/modules/fglrx/firegl_public.c: In function `__ke_agp_bind_memory':
/usr/src/modules/fglrx/firegl_public.c:3880: advarsel: videregiver den 1. parameter af henvisning til funktion fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c: In function `__ke_agp_unbind_memory':
/usr/src/modules/fglrx/firegl_public.c:3893: advarsel: videregiver den 1. parameter af henvisning til funktion fra en henvisningstype der ikke er forenelig med målets
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:2131: advarsel: 'deferred_flush' defineret, men aldrig brugt
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/modules/fglrx/.libfglrx_ip.a.GCC3.cmd for /usr/src/modules/fglrx/libfglrx_ip.a.GCC3
  LD [M]  /usr/src/modules/fglrx/fglrx.ko
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.12-10-686'
build succeeded with return value 0
ln: './fglrx.ko': Filen eksisterer
 compiling fglrx_agp.ko module
make.sh: line 873: cd: firegl_agpgart: Ingen sådan fil eller filkatalog
make: *** Ingen angivne mål og ingen makefil fundet. Stop.
AGPGART module build failed with return value 2
duplication skipped - generator was not called from regular lib tree
done.
==============================


Help help help! For the first it actually "feels" right :-/
On a sidenote agpgart is exactly the module that screws up when I try to use other howto's or even the prepackaged drivers.
I'm trying to do it with ati-drivers 8.20.8, and I've gotten this far. Please somebody help...

---

