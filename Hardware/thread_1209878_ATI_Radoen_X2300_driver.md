---
title: "ATI Radoen X2300 driver"
date: 2009-07-10
forum: Hardware
---

### Post by JonasKP on 2009-07-10
ATI Radeon mobility X2300
now! i know the deal with this that it might not work and all. but i thought of it and: shouldnt I be able to use the X1300 driver? as the X2300 is a modified X1300 that ATI does NOT support?

---

### Post by MaxTesla on 2009-10-30
Ok dude


I had the some problem with the ATI Mobility Radeon **[COLOR=#ff0000]X2300[/COLOR]** HD


And I got lucky and a smart dude told me what to do


But this was for the 9.04 and I got the advice some time ago but I wrote it all down but I do not remember all details just that it worked and if it fails you might have to do a complete reinstall so save all your stuff and do this


After every line press enter


[SIZE=3]Applications > Accesories > Terminal[/SIZE]


[SIZE=3]sudo apt-get install git-core[/SIZE]


[SIZE=3]sudo apt-get build-dep libdrm mesa[/SIZE]


[SIZE=3]git clone git://anongit.freedesktop.org/mesa/mesa[/SIZE]


[SIZE=3]cd mesa[/SIZE]


[SIZE=3]git checkout -b radeon-rewrite origin/radeon-rewrite[/SIZE]


[SIZE=3]./autogen.sh --prefix=/usr (Not needed)[/SIZE]


[SIZE=3]gedit configs/linux-dri[/SIZE]


[SIZE=3]Remove i810 i915 i965 mach64 mga r128 r200 s3v \ savage sis tdfx trident unichrome ffb swrast only r300 and radeon should stay take out the slash too only ---> DRI_DIRS = r300 radeon <--- left[/SIZE]


[SIZE=3]sudo apt-get install python-qt3-gl python-qt4-gl freeglut3[/SIZE]


[SIZE=3]sudo apt-get install qt3-dev-tools qt4-dev-tools[/SIZE]


[SIZE=3]sudo apt-get install xorg-dev[/SIZE]


[SIZE=3]sudo apt-get install build-essential libstdc++5[/SIZE]


[SIZE=3]make linux-dri-x86[/SIZE]


[SIZE=3]sudo cp lib/lib* /usr/lib && sudo cp lib/*_dri.so /usr/lib/dri[/SIZE]




[SIZE=3]sudo mkdir /usr/local/lib/dri && sudo cp lib/*_dri.so /usr/local/lib/dri[/SIZE]


[SIZE=3]Restart computer[/SIZE]

---

