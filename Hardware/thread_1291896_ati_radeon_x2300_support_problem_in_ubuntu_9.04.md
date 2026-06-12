---
title: "ati radeon x2300 support problem in ubuntu 9.04"
date: 2009-10-15
forum: Hardware
---

### Post by nidhinkrishnanv on 2009-10-15
When my system shuts down, it shows some error message saying there is some "hardware problem in PCI0" and screen becomes red and turns off. 

After updating my system the system is unable to get into the gui interface that is the loading screen  comes and some gradient colour change occurs.
What to do:confused::confused:

System-Sony vaio cr353
intel core 2 duo T8100
ati radeon X2300

---

### Post by MaxTesla on 2009-10-30
Ok dude


I had the some problem with the ATI Mobility Radeon X2300 HD


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

### Post by nidhinkrishnanv on 2009-11-06
when i tried the command 

[SIZE=3]git clone git://anongit.freedesktop.org/mesa/mesa

message :
Initialized empty Git repository in /home/nidhin/mesa/mesa/.git/
anongit.freedesktop.org[0: 131.252.210.176]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)

comes
[/SIZE]

---

