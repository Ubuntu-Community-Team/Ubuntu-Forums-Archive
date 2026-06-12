---
title: "Challenge: help me get Rage Mobility P/M with mach64 chip set DRI Working"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by narnie on 2007-04-10
I've been working several nights to get my video card DRI working so that I can ultimately install Beryl.

I was a dos diehard, and am familiar with cmd line in that. Compiling, as long as I have detail instruction, is fine with me, but I need that step-by-step.

My card reads:
00:14.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64)

Seems this should use the mach64 driver

I've read this forum link:

[http://ubuntuforums.org/showthread.p...bility+p%2F](http://ubuntuforums.org/showthread.p...bility+p%2F) m

Down toward the bottom, it says:

"btw, depending on your kernel version, the names in step 1 & 2 may vary"

I don't know how to change to what my kernal needs

I'm using ubuntu edgy 2.6.17-11-generic or 2.6.17-10-generic. Sorry, I don't now which.

When I try to follow the steps on the above link, I get this error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-2.6-686

When I look at Synaptic, I see several headers already marked as installed.

The next step is the wget step, but I don't now what snapshots I need for my kernal version. Perhaps I just need to use the most current.

Thanks in advance for any help.

Addendum:

I went on ahead and made sure I had all the apt-get stuff (just needed the linux-686 added).

I then compiled common without problems

Then I got an error with compiling mach64 that said something like "DRI drivers cannot be installed without the latest kernel modules" and told me to check out the error file as below:

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
CC [M] /tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.o
/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c: In function ‘drm_ati_free_pcigart_table’:
/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c:87: error: ‘struct page’ has no member named ‘count’
make[3]: *** [/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.o] Error 1
make[2]: *** [_module_/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/mach64/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

How do I get the "latest kernel modules?" Is the error log any help in helping me?

Thanks again

---

### Post by kfazz on 2007-04-13
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+ticket/4608](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+ticket/4608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				in order to get dri working for mach 64 theres two things you need to do:
build drm kernel modules from freedesktop.org
build a newer version of the xorg ati driver
(to install kernel headerstry:
sudo apt-get install linux-headers-generic)
you have to build a new version of the ati driver because teh drm module is a newer version than your current ati driver supports.

make a new directory to hold the drm and ati source
cd ~/Desktop
mkdir src
cd src

then install git if it isn't installed and downlaod latest drm:
git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm/linux-source
make DRM_MODULES="mach64"
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -a
sudo modprobe mach64

that takes care of getting the latest kernel modules, then for the driver:
first sudo aptitude or apt-get install autoconf-archive xorg-dev
cd ~/Desktop/src
wget [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.191.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.191.tar.bz2)
tar xvjf xf86-video-ati-6.6.191.tar.bz2
cd xf86-video-ati-6.6.191
./autogen.sh --prefix=/usr
make
sudo make isntall

then ctrl-alt-f1 and login, sudo /etc/init.d/gdm restart
(or kdm, whichever you use), and you should be good.
if cf86-video-ati doesn't build, you probably need to have some other package installed that i forgot to mention.

glxinfo | grep direct
and glxgears should give you an indicator as to it's working

btw: people say mach64 sucks as a 3d chip, but i've found the following to work great using dri acceleration that were useless using software mesa on teh same machine:
quake2 gl mode, zsnes

---

### Post by Old Pink on 2007-07-22
> **kfazz said:**
> **This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+ticket/4608](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+ticket/4608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
                in order to get dri working for mach 64 theres two things you need to do:
build drm kernel modules from freedesktop.org
build a newer version of the xorg ati driver
(to install kernel headerstry:
sudo apt-get install linux-headers-generic)
you have to build a new version of the ati driver because teh drm module is a newer version than your current ati driver supports.

make a new directory to hold the drm and ati source
cd ~/Desktop
mkdir src
cd src

then install git if it isn't installed and downlaod latest drm:
git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm/linux-source
make DRM_MODULES="mach64"
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -a
sudo modprobe mach64

that takes care of getting the latest kernel modules, then for the driver:
first sudo aptitude or apt-get install autoconf-archive xorg-dev
cd ~/Desktop/src
wget [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.191.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.191.tar.bz2)
tar xvjf xf86-video-ati-6.6.191.tar.bz2
cd xf86-video-ati-6.6.191
./autogen.sh --prefix=/usr
make
sudo make isntall

then ctrl-alt-f1 and login, sudo /etc/init.d/gdm restart
(or kdm, whichever you use), and you should be good.
if cf86-video-ati doesn't build, you probably need to have some other package installed that i forgot to mention.

glxinfo | grep direct
and glxgears should give you an indicator as to it's working

btw: people say mach64 sucks as a 3d chip, but i've found the following to work great using dri acceleration that were useless using software mesa on teh same machine:
quake2 gl mode, zsnes
[CENTER]**[COLOR=Red]DO NOT FOLLOW THIS GUIDE.[/COLOR]**
[/CENTER]
[B]
It is the worst written, most misspelt guess guide I've ever seen, which resulted in the destruction of my X installation, meaning when glxinfo is ran, the whole X system crashes. Also, it made no changes to the capability to direct render. Also, the packages half way through have been removed and give a 404 error. It is generally good practise to avoid this guide.
[/B]

---

### Post by dougfractal on 2007-07-24
In order to get DRI working for Mach64 you need to:

This is untested because I don't have a Mach64 card. It does compile.
Please let me know if in the Section "driver": driver "ati" needs to be : driver "mach64"

Setup compiler and libraries
make a new directory to hold the drm and ati source
download, build install and latest drm from freedesktop.org
download, build install and latest ati driver


Activate sudo
```

sudo echo "activating sudo rights"

``````

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev
SRCPATH=`pwd` 
cd $SRCPATH 
if [ -d 'src' ]; then echo -n ""; else mkdir src ; fi
cd src
if [ "$GIT" -neq '1' ] ; then git clone git://anongit.freedesktop.org/git/mesa/drm ; fi
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
else \ 
echo -e '\nIn a previous error I needed to comment out "/*  .... */" function static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,  unsigned long pfn) in drm/linux-core/drm_compat.c  lines 189-198 \n If this is the same error then do it.\nnano src/drm/linux-core/drm_compat.c\n'; \ 
GIT='1'; \
cd $SRCPATH;\
sleep 5; \
fi
# part two
cd $SRCPATH/src
if [ -f 'xf86-video-ati-6.6.192.tar.bz2' ]; then echo "already have xf86-video-ati"; else \
	wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.192.tar.bz2 ;     \
	tar xvjf xf86-video-ati-6.6.192.tar.bz2  ;\
fi
cd xf86-video-ati-6.6.192
./configure --prefix=/usr
make clean
make
sudo make install
cd $SRCPATH/
echo -e "\nsudo /etc/init.d/gdm restart\n"

```

---

### Post by zerwas on 2007-08-26
> **dougfractal said:**
> In order to get DRI working for Mach64 you need to:

This is untested because I don't have a Mach64 card. It does compile.
Please let me know if in the Section "driver": driver "ati" needs to be : driver "mach64"


THIS is the first tutorial that worked on my machine with Ubuntu Gutsy. "driver" needs to be "ati" :-).

Direct Rendering: Yes.

I copy n' pasted it line by line to see that everything worked. Thank you very much for this.

---

### Post by dougfractal on 2007-08-27
**Gusty update: using latest snapshot.**

In order to get DRI working for Mach64 you need to:

This is untested because I don't have a Mach64 card. It does compile.
Please let me know if in the Section "driver": driver "ati" needs to be : driver "mach64"

Setup compiler and libraries
make a new directory to hold the drm and ati source
download, build install and latest drm from freedesktop.org
download, build install and latest ati driver


edit the driver version to be the latest **xf86-video-ati** build from
[http://xorg.freedesktop.org/archive/individual/driver/](http://xorg.freedesktop.org/archive/individual/driver/)  
copy and paste this first (you can edit the driver version if you know of newer version) 
```

DRIVER_VS="6.7.195"

```
Activate sudo
```

sudo echo "activating sudo rights"

``````

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



Can you use my diagnostic tool as it will tell me lots of things about your setup.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by zerwas on 2007-09-14
You are doing a great work! I'd like to also use Compiz with my working card now. Do you know if that is possible?

The information you would like to have is attached to this post.

---

### Post by dougfractal on 2007-09-14
It feels good to help someone with an older card get dri.

you have compiz already installed so try 

> sudo apt-get install compiz compizconfig-settings-manager emerald  
compiz --replace &
ccsm 


> metacity --replace #to stop


see how it goes. I would think you could get Cube, previews, transpency.  gdesklets. cario-clock working. Though you only have 186 FPS.

You could try **default depth "16"  ** See if that speeds things up a bit. If it make a difference post your new frame rate ;-)

I've added you to my 3D card list.

---

### Post by Cadorna on 2007-10-26
Hi, could you help me with my Compaq Armada E500, Ati rage please ? Thanks.

---

### Post by dougfractal on 2007-10-27
You seem to have a drm problem.
try rebuilding it

> sudo echo "activating sudo rights"

> 
mkdir src
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm ;
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
fi 

echo -e "\nsudo /etc/init.d/gdm restart\n"

---

### Post by rbsis on 2007-10-27
I really want to use beryl please help me:)

---

### Post by oasick on 2007-10-28
Hi! I have a problem whit my 3D acceleration. I use your guide dougfractal ,[ this one]("http://ubuntuforums.org/showpost.php?p=3264969&postcount=6").

Compiled and install ok, but with glxgears appears this warnings:
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
libGL warning: 3D driver claims to not support visual 0x4b

Blender don't works and is very important for me... of course, i can't use compiz...

Can you help me? I have a compaq evo n400c and this is my graphic card from lshw:

description: VGA compatible controller
product: Rage Mobility P/M AGP 2x
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 64
width: 32 bits
clock: 33MHz
capabilities: agp agp-1.0 pm vga bus_master cap_list
configuration: driver=mach64 latency=66 mingnt=8 module=drm

videoram: 8mb

Very thank and i send the xinfo too.

---

### Post by dougfractal on 2007-10-28
oasick  you have 
dri Yes
and fps 289 
> (II) ATI(0): Direct rendering enabled
This is a good value for your card. There is no more that can be done with you card.
so what happens with
**compiz --replace &**

install ccsm (compiz config settings manager)
tweak some of the values.
ccsm

**metacity --replace & # to end**


what does blender do  (post output) It may be blender doesn't like AIGLX
there is a way to run an app on a different xorg.conf.

check out
[http://ubuntuforums.org/showthread.php?t=518426](http://ubuntuforums.org/showthread.php?t=518426)

---

### Post by dougfractal on 2007-10-28
> **rbsis said:**
> I really want to use beryl please help me:)


try the DRM install bit again.
> [drm] failed to load kernel module "mach64"
> 
Driver		"r128"
Identifier	"device1"
change the Driver		"ati"   in the xorg.conf   (both)

defaultdepth 16

---

### Post by rcoconnell on 2007-10-28
I have an old Ramline "Tablet" pc that I'm running Xubuntu/Edgy on.  lspci lists the video card as

```
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
```

Inspired by a suggestion on [this thread]("http://ubuntuforums.org/showthread.php?t=399724&highlight=ramline"), I decided to try to install the DRI drivers for the card.  It's currently set up as a digital picture frame, and I'd like to be able to have smooth transitions between pictures.

I started by trying to follow [staticeq2's]("http://ubuntuforums.org/showthread.php?t=7200") instructions, and ran into the usual problem with certain respositories not existing.  I made my best guess. and got the latest builds of the drivers -- 20060403, I think.  Fiddling around with updates left me with the 2.6.17-12-generic kernel, but unable to compile the mach64 drivers.

Just when I was ready to give up, I stumbled on [this post]("http://ubuntuforums.org/showthread.php?p=3090744&highlight=sed#post3090744").  Since I'd done most of what was in the script already, and didn't want to fiddle with the color depth, I just ran the two sed commands,

```
sed -i '87s\__put_page\put_page\' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c ; \
sed -i -e '51a\*/' -e '51i\/*' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c ; \
```

and then everything compiled -- hooray!!

Ah, but I'm still posting, right?

When I run GLXInfo, I now get:

```
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

```

Which sounds pretty bad!  Any suggestions?  I've attached the XInfo output here, and hope that it helps.

Thanks,
R

---

### Post by oasick on 2007-10-28
Thanks for your answer. This is the Blender error:

alvaro@alvaro-laptop:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
libGL warning: 3D driver claims to not support visual 0x4b
Ignoring Xlib error: error code 158 request code 146
Ignoring Xlib error: error code 158 request code 146
Mesa 7.0.1 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
Mesa 7.0.1 implementation error: User called no-op dispatch function (an unsupported extension function?)
Please report at bugzilla.freedesktop.org
/usr/bin/blender: line 46:   502 Fallo de segmentación  (core dumped) blender-bin "$@"


Thanks again!

---

### Post by lobiik on 2007-10-29
Hi, I used your  guide, but

```
make -C /lib/modules/2.6.18-custom/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.18'
  CC [M]  /src/drm/linux-core/drm_sysfs.o
/src/drm/linux-core/drm_sysfs.c: In function âdrm_sysfs_createâ:
/src/drm/linux-core/drm_sysfs.c:92: error: âstruct classâ has no member named âsuspendâ
/src/drm/linux-core/drm_sysfs.c:93: error: âstruct classâ has no member named âresumeâ
make[2]: *** [/src/drm/linux-core/drm_sysfs.o] Error 1
make[1]: *** [_module_/src/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.18'
make: *** [modules] Error 2
```


If I comment those two lines

```
       class->suspend = drm_sysfs_suspend;
        class->resume = drm_sysfs_resume;
```

then it say

```
  CC [M]  /src/drm/linux-core/drm_sysfs.o
/src/drm/linux-core/drm_sysfs.c:33: warning: âdrm_sysfs_suspendâ defined but not used
/src/drm/linux-core/drm_sysfs.c:52: warning: âdrm_sysfs_resumeâ defined but not used
```
and module compiles OK, but while loading:

```
FATAL: Error inserting mach64 (/lib/modules/2.6.18-custom/kernel/drivers/char/drm/mach64.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and dmesg:

```
[drm] Initialized drm 1.0.1 20051102
mach64: disagrees about version of symbol drm_open
mach64: Unknown symbol drm_open
mach64: disagrees about version of symbol drm_fasync
mach64: Unknown symbol drm_fasync
mach64: disagrees about version of symbol drm_poll
mach64: Unknown symbol drm_poll
mach64: disagrees about version of symbol drm_core_get_reg_ofs
mach64: Unknown symbol drm_core_get_reg_ofs
mach64: disagrees about version of symbol drm_pci_alloc
mach64: Unknown symbol drm_pci_alloc
mach64: disagrees about version of symbol drm_irq_uninstall
mach64: Unknown symbol drm_irq_uninstall
mach64: Unknown symbol drm_get_dev
mach64: disagrees about version of symbol drm_ioctl
mach64: Unknown symbol drm_ioctl
mach64: disagrees about version of symbol drm_exit
mach64: Unknown symbol drm_exit
mach64: Unknown symbol drm_getsarea
mach64: Unknown symbol drm_core_ioremapfree
mach64: disagrees about version of symbol drm_core_get_map_ofs
mach64: Unknown symbol drm_core_get_map_ofs
mach64: disagrees about version of symbol drm_init
mach64: Unknown symbol drm_init
mach64: disagrees about version of symbol drm_vbl_send_signals
mach64: Unknown symbol drm_vbl_send_signals
mach64: Unknown symbol drm_cleanup_pci
mach64: disagrees about version of symbol drm_pci_free
mach64: Unknown symbol drm_pci_free
mach64: Unknown symbol drm_core_ioremap
mach64: disagrees about version of symbol drm_mmap
mach64: Unknown symbol drm_mmap
mach64: disagrees about version of symbol drm_core_reclaim_buffers
mach64: Unknown symbol drm_core_reclaim_buffers
mach64: disagrees about version of symbol drm_release
mach64: Unknown symbol drm_release
mach64: disagrees about version of symbol drm_open
mach64: Unknown symbol drm_open
mach64: disagrees about version of symbol drm_fasync
mach64: Unknown symbol drm_fasync
mach64: disagrees about version of symbol drm_poll
mach64: Unknown symbol drm_poll
mach64: disagrees about version of symbol drm_core_get_reg_ofs
mach64: Unknown symbol drm_core_get_reg_ofs
mach64: disagrees about version of symbol drm_pci_alloc
mach64: Unknown symbol drm_pci_alloc
mach64: disagrees about version of symbol drm_irq_uninstall
mach64: Unknown symbol drm_irq_uninstall
mach64: Unknown symbol drm_get_dev
mach64: disagrees about version of symbol drm_ioctl
mach64: Unknown symbol drm_ioctl
mach64: disagrees about version of symbol drm_exit
mach64: Unknown symbol drm_exit
mach64: Unknown symbol drm_getsarea
mach64: Unknown symbol drm_core_ioremapfree
mach64: disagrees about version of symbol drm_core_get_map_ofs
mach64: Unknown symbol drm_core_get_map_ofs
mach64: disagrees about version of symbol drm_init
mach64: Unknown symbol drm_init
mach64: disagrees about version of symbol drm_vbl_send_signals
mach64: Unknown symbol drm_vbl_send_signals
mach64: Unknown symbol drm_cleanup_pci
mach64: disagrees about version of symbol drm_pci_free
mach64: Unknown symbol drm_pci_free
mach64: Unknown symbol drm_core_ioremap
mach64: disagrees about version of symbol drm_mmap
mach64: Unknown symbol drm_mmap
mach64: disagrees about version of symbol drm_core_reclaim_buffers
mach64: Unknown symbol drm_core_reclaim_buffers
mach64: disagrees about version of symbol drm_release
mach64: Unknown symbol drm_release
mach64: disagrees about version of symbol drm_open
mach64: Unknown symbol drm_open
mach64: disagrees about version of symbol drm_fasync
mach64: Unknown symbol drm_fasync
mach64: disagrees about version of symbol drm_poll
mach64: Unknown symbol drm_poll
mach64: disagrees about version of symbol drm_core_get_reg_ofs
mach64: Unknown symbol drm_core_get_reg_ofs
mach64: disagrees about version of symbol drm_pci_alloc
mach64: Unknown symbol drm_pci_alloc
mach64: disagrees about version of symbol drm_irq_uninstall
mach64: Unknown symbol drm_irq_uninstall
mach64: Unknown symbol drm_get_dev
mach64: disagrees about version of symbol drm_ioctl
mach64: Unknown symbol drm_ioctl
mach64: disagrees about version of symbol drm_exit
mach64: Unknown symbol drm_exit
mach64: Unknown symbol drm_getsarea
mach64: Unknown symbol drm_core_ioremapfree
mach64: disagrees about version of symbol drm_core_get_map_ofs
mach64: Unknown symbol drm_core_get_map_ofs
mach64: disagrees about version of symbol drm_init
mach64: Unknown symbol drm_init
mach64: disagrees about version of symbol drm_vbl_send_signals
mach64: Unknown symbol drm_vbl_send_signals
mach64: Unknown symbol drm_cleanup_pci
mach64: disagrees about version of symbol drm_pci_free
mach64: Unknown symbol drm_pci_free
mach64: Unknown symbol drm_core_ioremap
mach64: disagrees about version of symbol drm_mmap
mach64: Unknown symbol drm_mmap
mach64: disagrees about version of symbol drm_core_reclaim_buffers
mach64: Unknown symbol drm_core_reclaim_buffers
mach64: disagrees about version of symbol drm_release
mach64: Unknown symbol drm_release
mach64: disagrees about version of symbol drm_open
mach64: Unknown symbol drm_open
mach64: disagrees about version of symbol drm_fasync
mach64: Unknown symbol drm_fasync
mach64: disagrees about version of symbol drm_poll
mach64: Unknown symbol drm_poll
mach64: disagrees about version of symbol drm_core_get_reg_ofs
mach64: Unknown symbol drm_core_get_reg_ofs
mach64: disagrees about version of symbol drm_pci_alloc
mach64: Unknown symbol drm_pci_alloc
mach64: disagrees about version of symbol drm_irq_uninstall
mach64: Unknown symbol drm_irq_uninstall
mach64: Unknown symbol drm_get_dev
mach64: disagrees about version of symbol drm_ioctl
mach64: Unknown symbol drm_ioctl
mach64: disagrees about version of symbol drm_exit
mach64: Unknown symbol drm_exit
mach64: Unknown symbol drm_getsarea
mach64: Unknown symbol drm_core_ioremapfree
mach64: disagrees about version of symbol drm_core_get_map_ofs
mach64: Unknown symbol drm_core_get_map_ofs
mach64: disagrees about version of symbol drm_init
mach64: Unknown symbol drm_init
mach64: disagrees about version of symbol drm_vbl_send_signals
mach64: Unknown symbol drm_vbl_send_signals
mach64: Unknown symbol drm_cleanup_pci
mach64: disagrees about version of symbol drm_pci_free
mach64: Unknown symbol drm_pci_free
mach64: Unknown symbol drm_core_ioremap
mach64: disagrees about version of symbol drm_mmap
mach64: Unknown symbol drm_mmap
mach64: disagrees about version of symbol drm_core_reclaim_buffers
mach64: Unknown symbol drm_core_reclaim_buffers
mach64: disagrees about version of symbol drm_release
mach64: Unknown symbol drm_release
mach64: disagrees about version of symbol drm_open
mach64: Unknown symbol drm_open
mach64: disagrees about version of symbol drm_fasync
mach64: Unknown symbol drm_fasync
mach64: disagrees about version of symbol drm_poll
mach64: Unknown symbol drm_poll
mach64: disagrees about version of symbol drm_core_get_reg_ofs
mach64: Unknown symbol drm_core_get_reg_ofs
mach64: disagrees about version of symbol drm_pci_alloc
mach64: Unknown symbol drm_pci_alloc
mach64: disagrees about version of symbol drm_irq_uninstall
mach64: Unknown symbol drm_irq_uninstall
mach64: Unknown symbol drm_get_dev
mach64: disagrees about version of symbol drm_ioctl
mach64: Unknown symbol drm_ioctl
mach64: disagrees about version of symbol drm_exit
mach64: Unknown symbol drm_exit
mach64: Unknown symbol drm_getsarea
mach64: Unknown symbol drm_core_ioremapfree
mach64: disagrees about version of symbol drm_core_get_map_ofs
mach64: Unknown symbol drm_core_get_map_ofs
mach64: disagrees about version of symbol drm_init
mach64: Unknown symbol drm_init
mach64: disagrees about version of symbol drm_vbl_send_signals
mach64: Unknown symbol drm_vbl_send_signals
mach64: Unknown symbol drm_cleanup_pci
mach64: disagrees about version of symbol drm_pci_free
mach64: Unknown symbol drm_pci_free
mach64: Unknown symbol drm_core_ioremap
mach64: disagrees about version of symbol drm_mmap
mach64: Unknown symbol drm_mmap
mach64: disagrees about version of symbol drm_core_reclaim_buffers
mach64: Unknown symbol drm_core_reclaim_buffers
mach64: disagrees about version of symbol drm_release
mach64: Unknown symbol drm_release
```


Kernel is 2.6.18-custom

Any ideas?

---

### Post by Cadorna on 2007-10-29
Hi, I followed your suggestion, but it still not working !!!! What I'm doing wrong ? Here is my attach again ... please...help me ... why is so hard enable this function on Linux ....

---

### Post by dougfractal on 2007-10-30
**rcoconnell **  It looks as if you are using vesa not ati in your xorg.conf
> 
Section "Screen"
        Identifier	"Default Screen"
	Device		**"Generic Video Card"**
	Monitor		"Generic Monitor"

change to 
> Section "Screen"
        Identifier	"Default Screen"
	Device		**"ATI"**
	Monitor		"Generic Monitor"





 I grayed out my old instructions as it was old.   But if works good luck

---

### Post by dougfractal on 2007-10-30
> **Cadorna said:**
> Hi, I followed your suggestion, but it still not working !!!! What I'm doing wrong ? Here is my attach again ... please...help me ... why is so hard enable this function on Linux ....

> [drm] failed to load kernel module "mach64"
(II) ATI(0): [drm] drmOpen failed

Are you sure the drm part compiled?
try again.

---

### Post by dougfractal on 2007-10-30
**lobiik** do you need a custom kernel there is quite a choice already. SMP, lowlatency, RT....

try a non-custom and compile again ?

---

### Post by Cadorna on 2007-10-30
Sorry man, is my first week on Linux, I'm an oooooold Windows' user.I don't know how to do many things that you tell me, only copy & paste and simple stuffs like this ... I boot my machine in the non generic kernel option at boot start menu (I've got installed Win XP too). I have another issue, may be it has a relationshio with this problem (3D acceleration), when Ubuntu 7.10 is booting none image appears on screen, no bar progress, nothing. And after the system is ready and I  try to start a console with Ctrl+Alt+F4 for example, the screen fonts are sooo big that I can't see anything, is like a DOS version in 20 columns !!! Well, if you can help me step by step with this issues it will be great !!! I apologize for my english ...

---

### Post by dougfractal on 2007-11-01
> **Cadorna said:**
>  I  try to start a console with Ctrl+Alt+F4 for example, the screen fonts are sooo big that I can't see anything, is like a DOS version in 20 columns !!! Well, if you can help me step by step with this issues it will be great !!! I apologize for my english ...

** Re: Can I change the virtual console resoloution/font size**
In the boot loader menu append the following to the kernel line:

vga=791

or

vga=788

The first one is 1024x768 and the second is 800x600.



> **Cadorna said:**
> Sorry man, is my first week on Linux, I'm an oooooold Windows' user.I don't know how to do many things that you tell me, only copy & paste and simple stuffs like this ...

Just copy and paste the script from post 6.
[http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)

then check to see if this file as created.
**ls -l /lib/modules/`uname -r`/kernel/drivers/char/drm/mach64.ko**


good luck. let me know how it goes.

---

### Post by Cadorna on 2007-11-01
Hi, TKVM for your support. I had to modify some lines of the post #6 because it did't work in my Ubuntu 7.10, I mean, first, I'm logged into a terminal window with root credentials and then execute the following:

DRIVER_VS="6.7.195"
apt-get install linux-headers-generic build-essential
apt-get install autoconf-archive xorg-dev  git-core libdrm-dev
SRCPATH=`pwd` 
cd $SRCPATH 
mkdir src
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm
cd linux-core
make DRM_MODULES="mach64" 
cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
depmod -a
modprobe mach64
wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-$DRIVER_VS.tar.bz2
tar xvjf xf86-video-ati-$DRIVER_VS.tar.bz2
cd xf86-video-ati-$DRIVER_VS
./configure --prefix=/usr
make
make install
cd $SRCPATH/


buuuuuuut, I get some errors at the end of the process:

root@ARMADAE500:/src/drm/src/drm/linux-core/xf86-video-ati-6.7.195# make install
Making install in src
make[1]: se ingresa al directorio `/src/drm/src/drm/linux-core/xf86-video-ati-6.7.195/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -Wall -MT atibus.lo -MD -MP -MF ".deps/atibus.Tpo" -c -o atibus.lo atibus.c; \
        then mv -f ".deps/atibus.Tpo" ".deps/atibus.Plo"; else rm -f ".deps/atibus.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -Wall -MT atibus.lo -MD -MP -MF .deps/atibus.Tpo -c atibus.c  -fPIC -DPIC -o .libs/atibus.o
In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before 'GLboolean'
make[1]: *** [atibus.lo] Error 1
make[1]: se sale del directorio `/src/drm/src/drm/linux-core/xf86-video-ati-6.7.195/src'
make: *** [install-recursive] Error 1
root@ARMADAE500:/src/drm/src/drm/linux-core/xf86-video-ati-6.7.195# cd $SRCPATH/
root@ARMADAE500:/src/drm#

so, it didn't work ... **** !!!
I'm attaching the full text console output, thanks for your help again ...

---

### Post by dougfractal on 2007-11-02
Soulution:
from [http://ubuntuforums.org/showpost.php?p=3689922&postcount=185](http://ubuntuforums.org/showpost.php?p=3689922&postcount=185)
> make banged me with an error because gl.h was missing.

Code:

sudo apt-get install mesa-common-dev

---

### Post by Cadorna on 2007-11-02
Well, I fixed and ran it again and again and again ..., now everything seems to be right (see my attaches) but ... not 3d support.I try with "mach64" and "ati" driver section without succesfull ... Any idea ?

" glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)"

"Graphics Card:  ATI Technologies Inc Rage Mobility P/M AGP 2x 
CPU:            Pentium III (Coppermine)
Distribution:   Ubuntu 7.10
X version:      1.3.0
Driver:         ati ati
DRI:            No
GLX Server:     1.2
Resolution:     1024x768
Depth:          16
glxgears FPS:   257
Kernel:         2.6.22-14-386
UserName:       Cadorna
Xorg.conf:      xorg.conf.Cadorna.txt

Thank You again !!!

---

### Post by lobiik on 2007-11-03
ok, rm -rf / ed and started from scratch. Using 7.10 out of the box, I run that script (failed somewhere in the middle because of error on last row, so I did commands by keyboard. It works:

```
lobiik@evo:~$ glxinfo |grep direct
direct rendering: Yes
```

But...

```
lobiik@evo:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c4d (rev 64) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 
```

Tried everything I googled according to those errors. Still getting them. If I install xserver-xgl, then X doesn't come up at all. xorg.conf and Xorg log attached.

---

### Post by dougfractal on 2007-11-04
Cadorna and lobiik I'm glad you both getting somewhere with this.

**Cadorna** your xorg.log says you have direct rendering enabled but glxinfo says no. You do get 256FPS which is good for your card.

can you post the output
** ldd $(which glxgears)|grep libGL**

**lobiik** could you try with beryl as it may be a build version issue with CF
Also can tell me the line error in the script so that I can correct it.


Doug

---

### Post by deculpep on 2007-11-04
Graphics Card per lspci: ATI Technologies Inc Rage Mobility P/M (rev 64)
Well I followed dougfractal's guide in post #6 and everything complied cleanly (once I installed some dev packages).
...But now the ati x drivers give me no display, so I'm using the vesa ones.  If I start x with ati listed in my xorg.conf, then I get just a black screen and I can't even switch to a virtual console.  So I reboot in recovery mode and switch to vesa, and x and gdm start just fine.  The ati driver was working just fine for me before.

Anyways, here's the Xinfo output from dougfractal's tool, can someone help me sort this out?  I really got my hopes up about DRI with my older laptop.

---

### Post by dougfractal on 2007-11-05
**deculpep**  This might not work on all mach64 cards

I've tried to make a (mach64) card table here 
[http://ubuntuforums.org/showpost.php?p=3090792&postcount=162](http://ubuntuforums.org/showpost.php?p=3090792&postcount=162)


you could try the driver "ati" again
copy the /var/log/Xorg.0.log  to ~/
then go back to "vesa"  and post the log file

If you what to give up and go back to the old ati
> sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri

good luck

> (once I installed some dev packages). If you have the **history** can you post the dev packages so that I can include them.

---

### Post by lobiik on 2007-11-05
> **dougfractal said:**
> Cadorna and lobiik I'm glad you both getting somewhere with this.

**Cadorna** your xorg.log says you have direct rendering enabled but glxinfo says no. You do get 256FPS which is good for your card.

can you post the output
** ldd $(which glxgears)|grep libGL**

**lobiik** could you try with beryl as it may be a build version issue with CF
Also can tell me the line error in the script so that I can correct it.


Doug

That error, huh, don't remember exactly, but it was on line 26, for me last row. Also, it will be good, to add that mesa utils into that script to prevent having a problem with gl.h

Oh, and one thing. XGL server doesn't work for me. I only didn't try to remove complete xserver-xorg before it, but if I use it, gnome fails to load, if I try it with gnome-failsafe, it loads, but says, that XGL is no more required (or something like that) and how to disable it. GDM works OK, but when I login, screen remains dark, however it reacts (it's possible to safely restart laptop with pressing ctrl+alt+delete)


And as I googled more, compiz will not run on this card, because is quite old and doesn't support main  operations. Will try with beryl.

And by the way, getting 206fps with glxgears.


P.S.: I found nice looking how-to for beryl & xgl, so will try it for you, and if it will work without any problems, will create new thread with how-to to help users getting from those old compluter ladies as much as possible ;)

P.P.S.: It won't work if you will use Driver "mach64" - There must be Driver "ati"

---

### Post by Cadorna on 2007-11-07
Hi Doug ... sorry for the delay.

Here is the result of ldd $(which glxgears)|grep libGL:

 libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7f06000)

Thanks for your help.

---

### Post by dougfractal on 2007-11-07
I'm just guessing here

but my ldd $(which glxgears)|grep libGL:
>       libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ef1000)
       libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb731d000)

Now I have a nvidia card so I could be wrong,  however check the /usr/lib/  and maybe make a new symlink .  back up the old stuff , so you can undo any changes if it all goes wrong.

---

### Post by Cadorna on 2007-11-07
And how can I do that ? I mean, after I backed up this files, I must delete these and then ... ???? What must be do ??

---

### Post by dougfractal on 2007-11-08
This might be a wrong turn but.

ls /usr/lib/libGL*

if you have anything here try this.

mv /usr/X11R6/lib/libGL.so.1 /usr/X11R6/lib/libGL.so.1.old
ln -s /usr/lib/libGL.so.1 /usr/X11R6/lib/libGL.so.1

---

### Post by Cadorna on 2007-11-08
Yes !!! Yes !!! Yes !!! Yes !!! Yes !!! Yes !!! Yes !!!  It's works !!! Great !!!! Thank you very much for your support and patience !!!! Really !!!

 glxinfo | grep direct
direct rendering: Yes


Best Regards !!!!!

---

### Post by alphane on 2007-11-09
> Yes !!! Yes !!! Yes !!! Yes !!! Yes !!! Yes !!! Yes !!! It's works !!! Great !!!! Thank you very much for your support and patience !!!! Really !!!

glxinfo | grep direct
direct rendering: Yes

Does this now mean you can use Compiz and the like?

dougfractal - many many thanks for what you are doing here, it's people like you that make this forum work so well.

A quick question from myself.  I'm only a little past n00b status in terms of terminal, so this may be a little... simple... but:

After the line:
```
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
```

The terminal changes somehow from the normal $ prompt to a singular ">" prompt where the rest of the code is dumped, but not processed.

Any clues?

---

### Post by Cadorna on 2007-11-09
@alphane: Well, not really, it's only mean that 3D acceleration is now working. Now I'm fighting with Compiz & Beryl to try that they work, but this is another story.

Run this code (I was in the same problem that you respect to the line that you mentioned) in the post #24 ([http://ubuntuforums.org/showpost.php?p=3688216&postcount=24](http://ubuntuforums.org/showpost.php?p=3688216&postcount=24)) it works fine for me.

Regards.



----------------
Now playing: [Bryan Ferry And Roxy Music - Love Is The Drug](http://www.foxytunes.com/artist/bryan+ferry+and+roxy+music/track/love+is+the+drug)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by dougfractal on 2007-11-09
> **alphane said:**
> 
After the line:
```
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
```

The terminal changes somehow from the normal $ prompt to a singular ">" prompt where the rest of the code is dumped, but not processed.

Any clues?

(I've noticed to I had a missing fi now been added (whoops))

It's my coding style. I write the code to be dragged and dropped into terminal

```
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
fi
```

is the same as 
```

if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  sudo depmod -a; sudo modprobe mach64; fi
```

the other method is to provide a script.  but means create file, save file,  chmod file, run file.

Why do that when you can drag and drop :-)

(I don't know how I lost that fi)

---

### Post by dougfractal on 2007-11-09
duplicate post

---

### Post by foolsh on 2007-11-27
Even though I did not achieve "direct rendering: Yes" I have to thank the author of the guide here.  Because I was scared I was stuck with fiesty till I upgraded my secondary video card. I use two monitors and I couldn't get gusty to startx with the old ati driver configured for dual monitors for the life of me. thank you thank you thank you.

its an old, very old rage II pci card which should support dri but maybe not with xinerama.
this guide also fixed some screen glitches I had with fiesty on the ati screen.
I wonder why ubuntu's xorg ships with the crippled ati driver anyway?

thanks again you rock 
someone needs to sticky this thing so we can have it forever.

---

