---
title: "Apt-getting ATI drivers"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by fatal_boot on 2005-09-17
Hi,

I was wondering if there is an apt-get command to get the correct driver for a ATI X800XT-PE?

Thankyou,

Matt

---

### Post by krak on 2005-09-17
no i dont think you can get drivers via apt-get but below u have how i have installed my ATI drivers

[http://www.ubuntuforums.org/showthread.php?t=65276&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=65276&highlight=ATI)

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

i have mixed this 3 tutorials to install my ATI drivers. i have download 56mb .run file form ATI then 

sudo apt-get install fakeroot

xhost +
su
apt-get install build-essential
apt-get install linux-headers-$(uname -r)

after downloading linux-headers
i have made deb packages for ubuntu then by running, 
su
bash ati-driver-installer-8.16.20-i386.run
then "Generate Distribution Specific Driver Package"
choose what ubuntu do you use and generate packs

installing drivers
dpkg -i xorg-driver-fglrx_8.16.20-1_i386.deb
dpkg -i fglrx-kernel-source_8.16.20-1_i386.deb
dpkg -i fglrx-control_8.16.20-1_i386.deb (optional)

then do

cd /usr/src/modules/fglrx```
kek
``` 
./make.sh

mkdir /lib/modules/$(uname -r)/misc
cp fglrx.ko /lib/modules/$(uname -r)/misc/
depmod -ae

modprobe fglrx

now u have to generate xorg.conf file go [http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/)
after u have generated xorg.conf
cp /etc/X11/xorg.conf /etc/X11/xorg.bak
cd /etc/X11/
rm xorg.conf
nano xorg.conf
and copy and paste xorg.conf which u have generated at [http://www.objorkum.com/scripts/fglrxconfig/](http://www.objorkum.com/scripts/fglrxconfig/)
save you new xorg.conf
reset PC or X 
to check drivers working or not type fglrxinfo
you should get something like this

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

this is how i have installed my ATI drivers on Ubuntu 5.04 with buld in kernel 2.6.10-5-386
i have tried above tutorials but they didint fork for me probably i have done something wrong i use linux for a month only

---

