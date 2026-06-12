---
title: "Ati Rage and Dri"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by |iggy| on 2005-05-26
Hy everybody

At the first sorry for my bad English im from Germany  ;-) 

I have problems with installing the Dri Driver for the Ati card onboard 
my Compaq M700:

Kernel 2.6.10-5-686
VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

I can install Common Package but not the Dri Package here is the log:

Translation: I hope this will Help
Gehe in Verzeichnis = Go in Dir
Keine Regel = No Rules for create ...
Verlasse Verzeichnis = Close Dir
Fehler = Error

Here is the log of Dri.log

> make DRM_MODULES=mach64.o modules
make[1]: Gehe in Verzeichnis »/home/benny/Eigene Downloads/dripkg/drm/linux-core«
make -C /lib/modules/2.6.10-5-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
make[2]: *** Keine Regel, um »Downloads/dripkg/drm/linux-core« zu erstellen.  Schluss.
make[2]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
make[1]: *** [modules] Fehler 2
make[1]: Verlasse Verzeichnis »/home/benny/Eigene Downloads/dripkg/drm/linux-core«
make: *** [mach64.o] Fehler 2 

Compiling...
ERROR: Kernel modules did not compile

I had followed this Thread:
[HOWTO: enable 3d acceleration w/ Rage Mobility (mach64)](http://www.ubuntuforums.org/showthread.php?t=7200&page=1&pp=10&highlight=ati+rage+mobility) 

I hope you can Help me

---

