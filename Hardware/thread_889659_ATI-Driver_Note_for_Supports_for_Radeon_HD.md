---
title: "ATI-Driver Note for Supports for Radeon HD"
date: 2008-08-14
forum: Hardware
---

### Post by SnakeMedia on 2008-08-14
Hello dear Ubuntu- and other system-users,

I wish to tell about problems with Radeon HD-Drivers:

    * Radeon HD 2400
    * Radeon HD 2600 XT / Pro
    * Radeon HD 2900
    * Radeon HD 3xxx

Delete your old or worng ATI-Drivers ( x86 and x86_64)
I make sure with teminal: Please make to Superuser like Sudo!
```
apt-get purge fglrx-amdcccle fglrx-control fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
```Make sure with xorg.conf for nackup:
Copy from xorg-Configure to currect directory X11
```
cp /etc/X11/xorg.conf  /etc/X11&xorg.conf_bkp
```> Note: Do not forget this backup for xorg.conf!Edit your xorg-Configure: ```
gedit /etc/X11/xorg.conf
```Find "Section Device" and change "fglrx" to "ati"!
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection
```And edit your compiz-Desktop Effectte!
```
gedit /usr/bin/compiz
``````
# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T=""
BLACKLIST_PCIIDS="$T"
unset T
```Change to without "#"
```
# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T=""
BLACKLIST_PCIIDS="$T"
unset T
```[SIZE=5][COLOR=Red]**Note: Using with x86 ( 32 Bit and 64 Bit )**[/COLOR][/SIZE]
Please install required packages for compiling packages!
```
apt-get install module-assistant build-essential fakeroot dh-make debconf bzip2 wget debhelper libstdc++5 linux-headers-$(uname -r) ia32-* dkms cdbs orange libtool,
```I go in the directory now. ```
cd /var/tmp
```Download a latast ATI-Driver now! ```
wget -c --no-check-certificate https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-7-x86.x86_64.run
``` When a file is downloaded successfully.```
bash ati-driver-installer-8-4-x86.x86_64.run --extract fglrx
```Need to editing with drivers of Hardy / or another Ubuntu-part systems:> * Ubuntu Hardy:```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/hardy/xorg-driver-fglrx.preinst
```* Ubuntu Gutsy:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/gutsy/xorg-driver-fglrx.preinst
```* Ubuntu 8.04:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/8.04/xorg-driver-fglrx.preinst
```* Ubuntu 8.10:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/8.10/xorg-driver-fglrx.preinst
```* Ubuntu 7.10:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/7.10/xorg-driver-fglrx.preinst
```* Ubuntu Debian / Etch:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/intrepid/xorg-driver-fglrx.preinst
```Now can you change this:> # make new diversions
 dpkg-divert --add --rename --package $PKGNAME --divert /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 > /dev/null

 dpkg-divert --add --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/null

    if [ -n "$HAS_LIB32" ]; then
dpkg-divert --add --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1.2 > /dev/null
        [COLOR=Red]dpkg-divert --add --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null[/COLOR]

 dpkg-divert --add --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null
        [COLOR=Red]dpkg-divert --add --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1 > /dev/null[/COLOR]
    fi
    ;;

    abort-upgrade)
    ;;

    *)
        echo "preinst called with unknown argument \`$1'" >&2
        exit 0
    ;;
esac[/code]Than you can create a few simlinks and go to directory fglrx: ```
cd fglrxSave it!
Change this xorg-driver-fglrx.postrm now:> * Ubuntu Hardy:[code]gedit /var/tmp/fglrx/packages/Ubuntu/dists/hardy/xorg-driver-fglrx.postrm
```* Ubuntu Gutsy:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/gutsy/xorg-driver-fglrx.postrm
```* Ubuntu 8.04:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/8.04/xorg-driver-fglrx.postrm
```* Ubuntu 8.10:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/8.10/xorg-driver-fglrx.postrm
```* Ubuntu 7.10:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/7.10/xorg-driver-fglrx.postrm
```* Ubuntu Debian / Etch:
```
gedit /var/tmp/fglrx/packages/Ubuntu/dists/intrepid/xorg-driver-fglrx.postrm
```and this:> case "$1" in
    remove|purge)
 dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 > /dev/null

 dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1.2 > /dev/null

    [COLOR=#ff0000]dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null[/COLOR]

 dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null

    [COLOR=#ff0000]dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1 > /dev/null[/COLOR]

 dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/nullSave it!
[SIZE=5][COLOR=Red][B]Note about an architecture of processor![SIZE=4][COLOR=Black]
[/COLOR][/SIZE][/B][/COLOR][/SIZE]> [SIZE=5]For 32 Bit ( x86)[/SIZE]:
```
cd arch/x86/usr/X11R6
```Create few simlinks:```

ln -s lib lib
``` and put simlink: ```
ln -sf libfglrx_gamma.so.1.0 lib/libfglrx_gamma.so.1
```> [SIZE=5]For 64 Bit ( x86_64)[/SIZE]:
```
cd arch/x86_64/usr/X11R6
```Create few simlinks:```

ln -s lib64 lib
``` and put simlink: ```
ln -sf libfglrx_gamma.so.1.0 lib/libfglrx_gamma.so.1
```Go back to the fglrx directory!```
cd /var/tmp/fglrx
```And build a package by Ati Technology few minutes take place...
> * Ubuntu Hardy:```
bash packages/Ubuntu/ati-packager.sh --buildpkg hardy
```* Ubuntu Gutsy:```
bash packages/Ubuntu/ati-packager.sh --buildpkg gutsy
```* Ubuntu 8.04:```
bash packages/Ubuntu/ati-packager.sh --buildpkg 8.04
```* Ubuntu 8.10:```
bash packages/Ubuntu/ati-packager.sh --buildpkg 8.10
```* Ubuntu 7.10:```
bash packages/Ubuntu/ati-packager.sh --buildpkg 7.10
```* Ubuntu Debian / Etch:```
bash packages/Ubuntu/ati-packager.sh --buildpkg intreped
```And disable this fglrx in Disables_module
```
gedit /etc/default/linux-restricted-modules-common
```Add fglrx in ```
DISABLED_MODULES=""
to
DISABLED_MODULES="fglrx"
```Now go with debs from compiled packages!:
> [SIZE=5]For 32 Bit:[/SIZE]```
dpkg -i --force-overwrite xorg-driver-fglrx_8.512-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.512-0ubuntu1_i386.deb fglrx-kernel-source_8.512-0ubuntu1_i386.deb fglrx-amdcccle_8.512-0ubuntu1_i386.deb
```[SIZE=5]For 64 Bit:[/SIZE]```
dpkg -i --force-overwrite xorg-driver-fglrx_8.512-0ubuntu1_amd64.deb xorg-driver-fglrx-dev_8.512-0ubuntu1_amd64.deb fglrx-kernel-source_8.512-0ubuntu1_amd64.deb fglrx-amdcccle_8.512-0ubuntu1_amd64.deb
```4 debs will to install to modules copying and installing.

[SIZE=5][COLOR=Red]**Note:**[/COLOR][/SIZE] > What does it happen? If you have fglrx-modaliases_8.512-0ubuntu1_i386.deb for 32 Bit or fglrx-modaliases_8.512-0ubuntu1_amd64.deb for 64 Bit in our harddisk?
Please do not install! Let this file! Thanks!You might this error of deb:```
apt-get -f install
```Now create configures for Ati-Configure:
[LEFT] 1. Give this correct directory of xorg.cxnf! ```
aticonfig --initial --force --input=/etc/X11/xorg.conf
```[SIZE=5][COLOR=Red]**Note:**[/COLOR][/SIZE]> **Do not forget this resolution!!**Give this resolution!```
aticonfig --force --resolution=0,1280x1024,1024x768
```If you forget this resolution, than your computer was rebooted. It happens once **white screen** or **black screen**. 
Now aticonfig any option:
[SIZE=5][COLOR=Red]**Do not use this Overlay for Radeon HD!!!**[/COLOR][/SIZE]
Because OverLay can happen once next reboot to flicked screen. exmple Screensaver flicked always.. And do not switch with compiz-tools on! Sorry i found a bug of compiz. If compiz starts than it can happen with screensaver or Steam Simulator like HL1 or Half-Life 2 to flicked screen. If you want to leave this compiz on our computer or remove compiz-tools. Thanks

I hope that you understand about forbidden overlay from aticonfig.
Reboot it now!

---

Go to xorg.conf with sured option against flicked screen:```
gedit /etc/X11/xorg.conf
```Add new Options:> Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    [COLOR=Red]Option        "TexturedVideo" "off"[/COLOR]
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

[COLOR=Red]Section "Extensions"
    Option        "Composite" "1"
EndSection[/COLOR]Save it! And reboot now! (last time i swear)

---

Now I need to reverse the edits i did earlier to our compiz config.
```
gedit /usr/bin/compiz
``````
# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T=""
BLACKLIST_PCIIDS="$T"
unset T
```Change to with "#"
```
# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T=""
BLACKLIST_PCIIDS="$T"
unset T
```Check Ati-Driver-GLX now! ```
fglrxinfo
```An putput by my graphic card:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7769 Release
```Check with GLX-Info now! ```
glxinfo | grep direct
```An output is this:```
direct rendering: Yes
```Yeah it functions and works really. I hope that you are happy with graphic cards. I would you happy gaming or watching with Video Media or any things..

If you have problems of killing overlay or wrong driver than you can to answer me! Thanks. Please mark my post once sticky! Because new version of Radeon HD! A lot of thanks and have Fun!

Bye SnakeMedia
[/LEFT]

---

### Post by miecz on 2008-08-14
i am really new to ubuntu and i want to buy a laptop with a ati mobility radeon hd 3650 graphic card in it. My question is: Does your step by step instructions work for this video card or not?

---

### Post by SnakeMedia on 2008-08-14
> **miecz said:**
> i am really new to ubuntu and i want to buy a laptop with a ati mobility radeon hd 3650 graphic card in it. My question is: Does your step by step instructions work for this video card or not?

Hey dear miecz,
Video card can to work really. When you are using **mobily** grafic card. But can you try Screensaver? If your Graphic Card - Video screen did not plink. I am sure if your graphic card ATI Radeon HD 3650 supports really. If your drivers by ATI Technology is complet working.  Video = OpenGL ( like Texture 2D and 3D ) Do not worry! Did your screen of video plink / flick? If it flick not. Okay 

Okay. I hope that you can to buy new laptop.. Bye SnakeMedia

---

### Post by MasterJS on 2008-08-15
THANK YOU SO MUCH!!! This thread finally gave me the advice i needed to get the driver installed!

---

### Post by loseby on 2008-08-15
With the new 4870 cards out there will your system work with these cards ?

I have a 4870 and I want it to be as good under Linux as it is under Windows otherwise Ubuntu is a waste of space

---

### Post by XxLeekxX on 2008-08-27
Catalyst 8.8 has recently been released.  Do you recommend that I use that instead of the version 8.7?

---

### Post by eber69 on 2008-09-04
Hi!
I'm new to Linux. I'm just working my way through this guide. Have some questions:
1. There are differens instructions dep on version. I thought that v. 8.04 and Hardy Heron was the same. It seems I have both paths in my file structure. Wich instruction is for me?

2. I have a amd athlon 64 cpu. I should then do this:

cd arch/x86_64/usr/X11R6

I don't have this path. Is it something I've failed to do previously?

---

### Post by SnakeMedia on 2008-09-05
Sorry Do not forget for Arch with x64 sorry i have forgotten about important deb:

apt-get install ie32, lib32 or lib64 but i do not know i have3 been readden over 4 weeks.. 

Thanks , good dear user, MasterJS! Did your display driver work??

Radeon HD 4870 ( New card) Sould you download 8.8 versipon? A lot of thanks...

Bye SnakeMedia

---

### Post by wannapiece on 2008-09-07
Hi, I have a Toshiba with integrated Radeon 3100 graphics, will this work for this or is this only for dedicated mobility cards?

Thanks.

---

### Post by raygo22 on 2008-09-08
Hello, when I try sudo bash packages/Ubuntu/ati-packager.sh --buildpkg hardy I get this:

[Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.512-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
debian/rules:6: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/rules/debhelper.mk'.  Stop.
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

If i try it again i get:

Error: invalid package name passed to --buildpkg

What should i do?

---

### Post by SnakeMedia on 2008-09-13
Hi Wannapiece,
```
 
Toshiba with integrated Radeon 3100 graphics

```
 
No because it is old grafic card only normal not in **Radeon HD**!!!!!
 
If you have old version of **Radeon .... **, than you do not use **Radeon HD Posting**..
 
Ops... dear raygo22: Hmmm....
I think because you sould needed debians if you are trying, when it works failure. Than you must to install new and fresh Ubuntu once problems..
Or sould do you install **make** tools on Ubuntu ...
 
Or sould you <ati-driver....> --listpkg when does it not exist??
 
<ati-driver....> = your correct version of Ati-drivers 8.8
 
Thanks, do not worry!
 
Bye

---

