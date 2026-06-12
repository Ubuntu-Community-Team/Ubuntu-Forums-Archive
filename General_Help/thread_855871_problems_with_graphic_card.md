---
title: "problems with graphic card"
date: 2008-07-10
forum: General Help
---

### Post by tatoniss on 2008-07-10
I have a ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc) graphic card and would like to be able to use it. IN my search for trying to get it to work with compiz or just at all i found compiz-check. Compiz-check said that everything was OK but i did not think my dri was enabled. so i found a thread that i thought might work. I followed the process and it did not help now i cant even use the card without using a resolution of 600X600 which is way to small. is it possible to use the card at a higher resolution like 1024 x 768 also when the screens saver come on there is a box with  for white stripes and now compiz-check says this
```
tatoniss@Eric-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
 Driver in use:         ati
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): Operation not permitted
           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) 

``` they used to all say ok


Here is the instructions i followed
```
DRIVER_VS="6.8.192"

sudo echo "activating sudo rights"

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev  git-core libdrm-dev mesa-common-dev
SRCPATH=`pwd` 
cd $SRCPATH 
if [ -d 'src' ]; then echo -n ""; else mkdir src ; fi
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm ;
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
fi
if [ -f 'xf86-video-ati-$DRIVER_VS.tar.bz2' ]; then echo "already have xf86-video-ati"; else \
	wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-$DRIVER_VS.tar.bz2 ;     \
	tar xvjf xf86-video-ati-$DRIVER_VS.tar.bz2  ;\
fi
cd xf86-video-ati-$DRIVER_VS
./configure --prefix=/usr
make clean
make
sudo make install
cd $SRCPATH/
echo -e "\nsudo /etc/init.d/gdm restart\n"
```

Or is there a way to fix this

file that may have useful information

by the way I am kind of new at ubuntu
any help would be greatly appreciated

---

