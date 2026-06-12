---
title: "Display area out of alignment: Radeon HD 4350 (Ubuntu Studio 14.04.2)"
date: 2015-07-09
forum: Hardware
---

### Post by nfidia on 2015-07-09
Hi,

I think my problem is not limited to Ubuntu Studio 14.04.2. I guess it should also appear in other Ubuntu variants of Ubuntu 14.02. in combination with the hardware that I use.

I already described my request here:

[http://askubuntu.com/questions/643232/ubuntu-14-04-2-display-area-out-of-alignment](http://askubuntu.com/questions/643232/ubuntu-14-04-2-display-area-out-of-alignment)

, but nobody has answered to my request yet, since 7 days.

I think there are two possible solutions for this problem:

a) I need to create a /etc/X11/xorg.conf file, but I do not know what I should specify in this file, OR

b) Ubuntu needs to fix my problem by bugfixing the Ubuntu driver for my graphics card Radeon HD 4350 (this driver is or should be part of the Ubuntu packages "xserver-xorg-video-ati-Its-utopic" and/or "xserver-xorg-video-radeon-Its-utopic")

My question is:

What is more likely to be a solution for my problem? a) or b) ?

If you think a) is a possible solution, what should I specifiy in the /etc/X11/xorg.conf file?

If you think b) is the only solution, then I need to create a bug report on the appropriate Ubuntu web site.

Many thanks in advance.

---

### Post by dino99 on 2015-07-09
avoid the xorg.conf file, now the kernel directly deals with X
avoid the backported driver (lts) as there is to much issues (mainly ABI & drm)
purge the actual installed driver, then install back the driver from the ubuntu archive

---

### Post by nfidia on 2015-07-09
Hi dino99,

Thanks for your reply.

> **dino99 said:**
> avoid the xorg.conf file, now the kernel directly deals with X
avoid the backported driver (lts) as there is to much issues (mainly ABI & drm)

OK.

> purge the actual installed driver, then install back the driver from the ubuntu archive

How do I install the driver from the Ubuntu archive? I guess I need to specify a repository in the sources.list file
What is the name of this repository?
What is the name of the package that I should install, something with "radeon"?
And wouldn´t the installation of a driver from the archive cause a package conflict, mainly with the core X packages that are part of Ubuntu Studio 14.04.2?

Or do you mean with "archive" all current repositories that are part of Ubuntu 14.04.2?
If yes, I already purged the "Its-utopic"-drivers and re-installed them again. Effect: no change with regard to the issue I reported here.

---

### Post by nfidia on 2015-07-15
Hi,

Isn't there anybody who can help me? I am stuck with my problem since now 2 weeks.

More details regarding my problem:

If I want to install the "normal" Radeon driver, i.e. the package 

**xserver-xorg-video-radeon**

, then I get the following error message in Synaptic:

"Could not apply changes! Fix broken packages first!"

If I want to fix these packages in Synaptic via the Edit menu, "Fix broken packages", then I get this error message:

> E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

If I in Synaptic open the properties of the package 

**xserver-xorg-video-radeon**

, and within the properties the "Dependencies" tab, then the following packages are listed as dependencies:

- libc6 (>=2.17)
- libdrm-radeon1 (>=2.4.39)
- libglamor0
- libudev1 (>=183)
- xorg-video-abi-15
- xserver-xorg-core (>=2:1.14.99.902)
- Suggests: linux-firmware

All these packages are listed within Synaptic, i.e. are available for installation or are already installed, except for the package

**xorg-video-abi-15**

The package xorg-video-abi-15 is not shown in Synaptic, i.e. it is not available for installation.

Could it be that if the package 

**xorg-video-abi-15 **

would be available for installation, that then I could install the package

**xserver-xorg-video-radeon**

?

I strongly guess so.

So doesn't Canonical need to provide the package

**xorg-video-abi-15 **

in its repositories for Ubuntu (Studio) 14.04, so that I would be able to install the package

**xserver-xorg-video-radeon**

?

What is your opinion about this?

---

### Post by Bashing-om on 2015-07-15
nfidia; Hello: 

Let's do this from terminal, as that is where we work the better.
1st the background on this situation:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.

Terminal command -> 
```

X -version

```
to determine the x-server version.

So now we know we must remove all vestiges of the FGLRX driver and install the open source driver "radeon" :
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Reboot to see the effect. I do expect ->
[INDENT][INDENT]shinning like a new penny
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-15
Bashing-Om, thanks for your support.

My X Server Version is X.Org X Server 1.16.0

I executed the commands one after another that you specified. But when I execute the following command:

> sudo apt-get install xserver-xorg-video-radeon

, then I get the following result:

> jrad@music:~/Schreibtisch$ sudo apt-get install xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 xserver-xorg-video-radeon : Depends: xorg-video-abi-15
                             Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.
jrad@music:~/Schreibtisch$ 


I guess the reason for this is the fact that the following packages have automatically been installed by the Ubuntu installation routine:

xserver-xorg-core-Its-utopic
xserver-xorg-input-all-Its-utopic
xserver-xorg-input-evdev-Its-utopic
xserver-xorg-input-mouse-Its-utopic
xserver-xorg-input-synaptics-Its-utopic
xserver-xorg-input-vmmouse-Its-utopic
xserver-xorg-input-wacom-Its-utopic
**xserver-xorg-Its-utopic**
xserver-xorg-video-cirrus-Its-utopic
xserver-xorg-video-fbdev-Its-utopic
xserver-xorg-video-intel-Its-utopic
xserver-xorg-video-mach64-Its-utopic
xserver-xorg-video-mga-Its-utopic
xserver-xorg-video-modesetting-Its-utopic
xserver-xorg-video-neomagic-Its-utopic
xserver-xorg-video-nouveau-Its-utopic
xserver-xorg-video-openchrome-Its-utopic
xserver-xorg-video-r128-Its-utopic
xserver-xorg-video-r128-Its-utopic-dbg
[B]xserver-xorg-video-radeon-Its-utopic
xserver-xorg-video-radeon-Its-utopic-dbg[/B]
xserver-xorg-video-savage-Its-utopic
xserver-xorg-video-siliconmotion-Its-utopic
xserver-xorg-video-sisusb-Its-utopic
xserver-xorg-video-tdfx-Its-utopic
xserver-xorg-video-trident-Its-utopic
xserver-xorg-video-vesa-Its-utopic
xserver-xorg-videovmware-Its-utopic

I strongly guess that I first need to remove all these "Its-utopic" packages in order to install the package xserver-xorg-video-radeon, together with the core package(s) of the X server.

But how do I do that?

Best regards,

nfidia

---

### Post by nfidia on 2015-07-15
This is a possible answer to my question in my last post:

1. Open a console using CTRL+ALT+F1 (Note that I cannot see the whole console, the left part of the display area is left from the left edge of my screen, so I cannot see the prompt)

2. Execute "sudo apt-get purge xserver-xorg-Its-utopic"". This should remove all important "Its-utpic" dependencies.

3. Execute "sudo apt-get install xserver-xorg-video-radeon" and continue with the command list as specified by @Bashing-om, and then reboot.

Would this be the right procedure?

---

### Post by Bashing-om on 2015-07-15
nfidia; Humm ..

Like you I am not real sure how to proceed with this (xserver-xorg-video-radeon : Depends: xorg-video-abi-15) .

Think'n and look'n.

[INDENT][INDENT]soonest I know better
[INDENT][INDENT][INDENT]I will be back
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-15
nfidia; Humm ...

 We may be stuck .. do not know yet, but:
```

apt-cache search xorg-video-abi-

```
tells us that " xorg-video-abi-15 " is a part of " xserver-xorg-core " and " xserver-xorg-core-lts-utopic " .

Let's see what is going to happen IF we remove it:
```

sudo apt-get remove -s xserver-xorg-core-lts-utopic

``` where the -s flag is "simulate" but do not do it !

And we want to know the version of " xserver-xorg-core " that is presently installed:
```

dpkg -l xserver-xorg-core

```

See if we can finger out sumpthin

---

### Post by nfidia on 2015-07-16
Hi bashing-om,

Thank you again for your support.

> **Bashing-om said:**
> nfidia; Humm ...

 We may be stuck .. do not know yet, but:
```

apt-cache search xorg-video-abi-

```
tells us that " xorg-video-abi-15 " is a part of " xserver-xorg-core " and " xserver-xorg-core-lts-utopic " .

Yes, I found that out, too. xorg-video-abi-15 is a so-called virtual package. Could it be that xorg-video-abi-15 is missing in xserver-xorg-core and xserver-xorg-core-lts-utopic?

This command:
```

sudo apt-get remove -s xserver-xorg-core-lts-utopic

```

results on my machine in:

```
jrad@music:~/Schreibtisch$ sudo apt-get remove -s xserver-xorg-core-lts-utopic
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gstreamer1.0-gnonlin
  kdenlive-data krita-data libakonadi-kde4 libakonadiprotocolinternals1
  libappindicator1 libastro1 libbonoboui2-0 libbonoboui2-common
  libboost-python1.54.0 libcauchy0.0 libcolord-gtk1 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libltc11
  liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data libmlt6
  libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-30-lowlatency linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  marble-data marble-plugins melt mencoder mypaint-data openshot-doc
  phatch-cli python-appindicator python-dateutil python-gnome2 python-gst-1.0
  python-hachoir-core python-hachoir-metadata python-hachoir-parser
  python-kaa-base python-kaa-metadata python-matplotlib python-matplotlib-data
  python-mlt python-pyexiv2 python-pyexiv2-doc python-pygoocanvas
  python-pyorbit python-pyparsing python-sqlite python-support python-tz
  rawtherapee-data transcode transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
Suggested packages:
  libglide3 xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze
  firmware-linux
The following packages will be REMOVED
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gtkclutter-1.0 gir1.2-totem-1.0
  gstreamer1.0-clutter libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libopenvg1-mesa-lts-utopic libtotem0 libwayland-egl1-mesa-lts-utopic
  libxatracker2-lts-utopic totem totem-mozilla totem-plugins
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mach64-lts-utopic-dbg xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-r128-lts-utopic-dbg xserver-xorg-video-radeon-lts-utopic
  xserver-xorg-video-radeon-lts-utopic-dbg
  xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
The following NEW packages will be installed
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
0 to upgrade, 33 to newly install, 56 to remove and 0 not to upgrade.
Remv gir1.2-gtkclutter-1.0 [1.4.4-3ubuntu2.2]
Remv gir1.2-clutter-gst-2.0 [2.0.8-1build1]
Remv gir1.2-clutter-1.0 [1.16.4-0ubuntu2]
Remv gir1.2-coglpango-1.0 [1.16.2-1]
Remv gir1.2-cogl-1.0 [1.16.2-1]
Remv totem-plugins [3.10.1-1ubuntu4]
Remv gir1.2-totem-1.0 [3.10.1-1ubuntu4]
Remv totem-mozilla [3.10.1-1ubuntu4]
Remv totem [3.10.1-1ubuntu4]
Remv gstreamer1.0-clutter [2.0.8-1build1]
Remv libtotem0 [3.10.1-1ubuntu4]
Remv libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2]
Remv libclutter-gst-2.0-0 [2.0.8-1build1]
Remv libclutter-1.0-0 [1.16.4-0ubuntu2]
Remv libcogl-pango15 [1.16.2-1]
Remv libcogl15 [1.16.2-1]
Remv libegl1-mesa-drivers-lts-utopic [10.3.2-0ubuntu1~trusty2]
Remv libwayland-egl1-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2]
Remv xserver-xorg-video-vesa-lts-utopic [1:2.3.3-1build2~trusty1]
Remv xserver-xorg-video-trident-lts-utopic [1:1.3.6-0ubuntu6~trusty1]
Remv xserver-xorg-video-tdfx-lts-utopic [1:1.4.5-1build2~trusty1]
Remv xserver-xorg-video-sisusb-lts-utopic [1:0.9.6-2build2~trusty1]
Remv xserver-xorg-video-siliconmotion-lts-utopic [1:1.7.7-2build2~trusty1]
Remv xserver-xorg-video-savage-lts-utopic [1:2.3.7-2ubuntu3~trusty1]
Remv xserver-xorg-video-radeon-lts-utopic-dbg [1:7.4.0-2ubuntu2~trusty1]
Remv xserver-xorg-video-radeon-lts-utopic [1:7.4.0-2ubuntu2~trusty1]
Remv xserver-xorg-video-r128-lts-utopic-dbg [6.9.2-1build2~trusty1]
Remv xserver-xorg-video-r128-lts-utopic [6.9.2-1build2~trusty1]
Remv xserver-xorg-video-openchrome-lts-utopic [1:0.3.3-1build2~trusty1]
Remv xserver-xorg-video-nouveau-lts-utopic [1:1.0.11-1ubuntu2~trusty1]
Remv xserver-xorg-video-neomagic-lts-utopic [1:1.2.8-1build2~trusty1]
Remv xserver-xorg-video-modesetting-lts-utopic [0.9.0-1build1~trusty1]
Remv xserver-xorg-video-mga-lts-utopic [1:1.6.3-2build1~trusty1]
Remv xserver-xorg-video-mach64-lts-utopic-dbg [6.9.4-2~trusty1]
Remv xserver-xorg-video-mach64-lts-utopic [6.9.4-2~trusty1]
Remv xserver-xorg-video-intel-lts-utopic [2:2.99.914-1~exp1ubuntu4.3~trusty1]
Remv xserver-xorg-video-fbdev-lts-utopic [1:0.4.4-1build2~trusty1]
Remv xserver-xorg-video-cirrus-lts-utopic [1:1.5.2-2build1~trusty1]
Remv xserver-xorg-input-all-lts-utopic [1:7.7+7ubuntu2~trusty1]
Remv xserver-xorg-input-wacom-lts-utopic [1:0.25.0-0ubuntu1~trusty1]
Remv xserver-xorg-input-vmmouse-lts-utopic [1:13.0.0-1build2~trusty1]
Remv xserver-xorg-input-synaptics-lts-utopic [1.8.1-1ubuntu1~trusty1]
Remv xserver-xorg-input-mouse-lts-utopic [1:1.9.0-1build2~trusty1]
Remv xserver-xorg-input-evdev-lts-utopic [1:2.9.0-1ubuntu2~trusty1] [xserver-xorg-lts-utopic:i386 ]
Remv xserver-xorg-core-lts-utopic [2:1.16.0-1ubuntu1.2~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xserver-xorg-lts-utopic:i386 ]
Remv libxatracker2-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xserver-xorg-lts-utopic:i386 ]
Remv libopenvg1-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xserver-xorg-lts-utopic:i386 ]
Remv libgles2-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xserver-xorg-lts-utopic:i386 gstreamer1.0-plugins-bad:i386 ]
Remv xserver-xorg-lts-utopic [1:7.7+7ubuntu2~trusty1] [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 gstreamer1.0-plugins-bad:i386 ]
Inst libgles2-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386]) [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libgles1-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libgl1-mesa-glx-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 libftgl2:i386 libqt4-opengl:i386 libxine2-x:i386 xorg:i386 libgtkglext1:i386 libglew1.10:i386 libopencv-core2.4:i386 libwebkitgtk-3.0-0:i386 audacious-plugins:i386 x11-utils:i386 phonon-backend-gstreamer:i386 libvisual-0.4-plugins:i386 xscreensaver-gl:i386 libqtwebkit4:i386 gem:i386 gimp-plugin-registry:i386 libva-glx1:i386 libglu1-mesa:i386 freeglut3:i386 libfltk1.1:i386 libopencv-highgui2.4:i386 mplayer:i386 libwxgtk2.8-0:i386 libglamor0:i386 pd-pdp:i386 blender:i386 libwebkitgtk-1.0-0:i386 ]
Inst libgl1-mesa-glx (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386]) [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libglapi-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libegl1-mesa-lts-utopic [10.3.2-0ubuntu1~trusty2] [libgstreamer-plugins-bad1.0-0:i386 xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 gstreamer1.0-plugins-bad:i386 ]
Inst libegl1-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386]) [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libgbm1-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv libgl1-mesa-dri-lts-utopic [10.3.2-0ubuntu1~trusty2] [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 libgbm1:i386 ]
Inst libgl1-mesa-dri (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386]) [xserver-xorg-video-vmware-lts-utopic:i386 xorg:i386 ]
Remv xserver-xorg-video-vmware-lts-utopic [1:13.0.2-3ubuntu1~trusty1] [xorg:i386 ]
Inst xserver-xorg (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libglapi-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386]) []
Inst xserver-xorg-core (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [i386]) []
Inst xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst xserver-xorg-video-intel (2:2.99.910-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386]) []
Inst xserver-xorg-video-vesa (1:2.3.3-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-trident (1:1.3.6-0ubuntu5 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-tdfx (1:1.4.5-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-sisusb (1:0.9.6-2build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-sis (1:0.10.7-0ubuntu6 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-siliconmotion (1:1.7.7-2build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-savage (1:2.3.7-2ubuntu2 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-s3 (1:0.6.5-0ubuntu4 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-r128 (6.9.2-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-qxl (0.1.1-0ubuntu3 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-openchrome (1:0.3.3-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-nouveau (1:1.0.10-1ubuntu2 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-neomagic (1:1.2.8-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-modesetting (0.8.1-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-mga (1:1.6.3-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-mach64 (6.9.4-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-fbdev (1:0.4.4-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-video-cirrus (1:1.5.2-1build1 Ubuntu:14.04/trusty [i386]) []
Inst xserver-xorg-input-evdev (1:2.8.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst xserver-xorg-input-synaptics (1.7.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst xserver-xorg-input-mouse (1:1.9.0-1build1 Ubuntu:14.04/trusty [i386])
Inst xserver-xorg-input-vmmouse (1:13.0.0-1build1 Ubuntu:14.04/trusty [i386])
Inst xserver-xorg-input-wacom (1:0.23.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst xserver-xorg-input-all (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [i386])
Conf libglapi-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386])
Conf libgles2-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386])
Conf libgl1-mesa-glx (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386])
Conf libegl1-mesa (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386])
Conf libgl1-mesa-dri (10.1.3-0ubuntu0.4 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg-core (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg-video-intel (2:2.99.910-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg-video-vesa (1:2.3.3-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-trident (1:1.3.6-0ubuntu5 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-tdfx (1:1.4.5-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-sisusb (1:0.9.6-2build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-sis (1:0.10.7-0ubuntu6 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-siliconmotion (1:1.7.7-2build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-savage (1:2.3.7-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-s3 (1:0.6.5-0ubuntu4 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-r128 (6.9.2-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-qxl (0.1.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-openchrome (1:0.3.3-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-nouveau (1:1.0.10-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-neomagic (1:1.2.8-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-modesetting (0.8.1-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-mga (1:1.6.3-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-mach64 (6.9.4-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-fbdev (1:0.4.4-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-video-cirrus (1:1.5.2-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-evdev (1:2.8.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-synaptics (1.7.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-mouse (1:1.9.0-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-vmmouse (1:13.0.0-1build1 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-wacom (1:0.23.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf xserver-xorg-input-all (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [i386])
Conf xserver-xorg (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [i386])
jrad@music:~/Schreibtisch$ 
```

This command:
```

dpkg -l xserver-xorg-core

```

results on my machine in:

> jrad@music:~/Schreibtisch$ dpkg -l xserver-xorg-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-========================================
un  xserver-xorg-core <none>        <none>        (no description available)
jrad@music:~/Schreibtisch$ 

---

### Post by Bashing-om on 2015-07-16
nfidia; Yikes !

I am not afraid of anything, and this makes my hair stand up. If we proceed, a lot of change. And with HWE at play here I do not know what the effect will be. There is no reverting back once (H)ard(W)are (E)nablement is implemented. These changes are more than my little mind can comprehend.

Back up your data, and we rip out the heart of the Xserver layer, and try and rebuild it.
It will interesting to say the least.

If it is any consolation, with the data backed up, one can always take the nuclear solution and (RE-)install the operating system . But, I surely hate when that happens. We learn little from that expedient .

Getting the open source driver installed in this situation may be a long long process, fraught with peril. I do assure you we will learn from the experience, and it is likely that we will succeed .

However, if time and use-of-the-system is a factor, maybe best to (RE-)install and be up and running in a matter of minutes.

My thoughts presently: We do know we have this situation:
> 
The following packages have unmet dependencies.
xserver-xorg-video-radeon : Depends: xorg-video-abi-15
Depends: [color=red]xserver-xorg-core[/color] (>= 2:1.14.99.902)


and it is not installed:
> 
un xserver-xorg-core <none> <none> (no description available)


So we do know we must find a means to install " xserver-xorg-core " OR something that will work in it's place .


[INDENT][INDENT]Me, I am all for the learning experience
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-16
Hi Bashing-om,

> **Bashing-om said:**
> I am not afraid of anything, and this makes my hair stand up. If we proceed, a lot of change. And with HWE at play here I do not know what the effect will be. There is no reverting back once (H)ard(W)are (E)nablement is implemented. These changes are more than my little mind can comprehend.

What is this HWE? Is this a BIOS feature? Or is this a future functionality of Linux distros, or of Ubuntu only?

> Back up your data

There is nothing to back up, because I could not use my Ubuntu Studio 14.04.02 installation for productive means.

> and we rip out the heart of the Xserver layer, and try and rebuild it.
It will interesting to say the least.

Let's do it ;)

> If it is any consolation, with the data backed up, one can always take the nuclear solution and (RE-)install the operating system . But, I surely hate when that happens. We learn little from that expedient .

I agree.

If I need to do a re-installation, then I either bring my computer to the hospital or throw it out of the window :-D

> Getting the open source driver installed in this situation may be a long long process, fraught with peril. I do assure you we will learn from the experience, and it is likely that we will succeed .

Ok.

> However, if time and use-of-the-system is a factor, maybe best to (RE-)install and be up and running in a matter of minutes.

No, I prefer the uneasy solution: Find out the reason for this bug, and find a workaround for it, and then hopefully get this bug fixed by Canonical.

> So we do know we must find a means to install " xserver-xorg-core " OR something that will work in it's place .

What's with that abi-package? Don't we first need to make sure that it is available?

> Me, I am all for the learning experience

Let's do it ;)

So what shall I exactly do? I know that I need to completely remove all xserver/xorg-*-Its-utopic packages, and then install the non-Its-utopic packages of Xserver/Xorg. Thus, I need to use a console which I open f.e. via CTRL+ALT-F1 because I will destroy the graphical user interface.

Best regards,

nfidia

---

### Post by nfidia on 2015-07-16
> **nfidia said:**
> So what shall I exactly do? I know that I need to completely remove all xserver/xorg-*-Its-utopic packages, and then install the non-Its-utopic packages of Xserver/Xorg. Thus, I need to use a console which I open f.e. via CTRL+ALT-F1 because I will destroy the graphical user interface.

There is one "little" problem with this approach: If I open a console using f.e. CTRL+ALT-F1, then I do not see the prompt. Because the display area is moved to the left, i.e. the prompt is located left from the left edge of my monitor. So I need to blindly type in commands (this is not a real problem), but I cannot see / I only partly see the results of my commands. So I will not know what my machine wants from me if I have to interact with the operating system as the result of a certain command.

---

### Post by Bashing-om on 2015-07-16
nfidia; OK !

Let's do this.

Let's get us a terminal we can work with . Try this: - a bit of a pain but .....
Reboot the system to the grub menu and with the latest kernel choice selected (asterisk) press the 'e' key for edit mode ->
Boot parameters screen, arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and arrow across to the terms "quiet splash" and replace these terms with the term " text " - without the quotes .
Press key combo ctl+x to continue the boot process to TTY1 . Log in here with your username and password ( no response to the screen when password is enter, enter password blindly and hit the enter key) .

If now at this terminal (TTY1) you have a full display that is completely functional, we will make this a permanent arrangement until such time as we have the GUI repaired . This so we can continue our work .

As to what we are going to do about " xorg-video-abi-15 " do not know yet . Best case scenario is when we get "xserver-xorg-core " installed that need will go away (?) .

HWE:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

As said, I do not know how the elevated kernel, libs, and xserver will play out here trying to install the opensource driver . Maybe this driver is built for a mainstream kernel ?? I am willing to learn better.

Get us to a terminal we can work from ...
[INDENT][INDENT][INDENT]and away we go
[/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-17
Hi Bashing-om,


> **Bashing-om said:**
> Let's get us a terminal we can work with . Try this: - a bit of a pain but .....

That's no problem for me.

> Reboot the system to the grub menu and with the latest kernel choice selected (asterisk) press the 'e' key for edit mode ->
Boot parameters screen, arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and arrow across to the terms "quiet splash" and replace these terms with the term " text " - without the quotes .
Press key combo ctl+x to continue the boot process to TTY1 . Log in here with your username and password ( no response to the screen when password is enter, enter password blindly and hit the enter key) .

I followed your instructions, and the result is:

A TTY in which I cannot see the prompt. Same visual effect as if I would open a console using CTRL+ALT+F1 in a X-server based desktop environment, i.e. the display area is moved to the left, so that the prompt is located left from the left edge of my monitor (a TV screen). In this TTY1 which I had created I typed in the command "reboot" (sorry, I once in w while forget the preceding "sudo", because I am used to Debian). The result was that I could only see the letters "oot" of what I had typed in (i.e. the word "reboot").

Please note that I do not know the exakt meaning of the word "prompt" because my mother language is not English. To be more precisely: I cannot see the left edge of the prompt, i.e. I cannot see the following letters:

> root@samba:~#

(this is a quote from my Debian installation where I do not have that display problem)

, and the first two letters of a command that I type in (see above and the command "reboot").

Because I did not start X, but started Ubuntu in text mode, and the display problem occured again, I think that the reason for this behaviour is not X-related, but related to a software component that is started/used before X gets started.

By the way, whenever I start Ubuntu 14.04.2 (the following is for sure the case for the low latency kernel), after selecting the low latency kernel in den grub menu list, my monitor first turns black, and then, after a while, while Ubuntu is loading, my TV screen (my monitor) tells me via a TV message that there is "no signal" and still keeps black. After a while this message dissappears, and then either X is displayed after a while, or TTY1 is displayed (as the result of the last boot, as described above).

> As to what we are going to do about " xorg-video-abi-15 " do not know yet . Best case scenario is when we get "xserver-xorg-core " installed that need will go away (?).

As said above, I strongly guess that the behaviour has nothing to do with X, so I guess we do not need to fix the "xorg-video-abi-15" issue. At least for now.

> HWE:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Thanks for the link. So all this "Its Utopic" stuff are features from a newer Ubuntu release (14.10)?

How about getting the "Its present" stuff installed on my machine? :-D ;)

---

### Post by Bashing-om on 2015-07-17
nfidia; Trails troubles and tribulations;

We try and work with what we have to work with.
By the way, your command of the English language is admirable, you do well . English is the only language I am able to converse in, and sometimes not too well .

I do not think it is possible to revert a system back from (H)ard(W)are (E)nablement. IF required to have and use the original kernel, we would have to (RE-)install and make sure the install is release 14.04[color=green].1[/color]. This so far as I know, perhaps others can advise if this is not the fact.

Presently, I think the focus of our attention is to get Xorg functional, and then be able to install the open source driver.
With the situation of not able to see the complete outputs in terminal, let's get an alternate means to see and relay these outputs -> we use our paste site for this purpose:
```

sudo apt-get install pastebinit

```

I think, now, we want to know how the system responds and what the advise from the system is when we attempt to install that required dependency, xserver-xorg-core  .
```

sudo apt-get install xserver-xorg-core | pastebinit

```
The result from the package manager will be output to the pastebin site. The site will give you a URL back in terminal. Can you see enough of this URL to relay that URL back here to the thread ?
As an example of how 'pastebinit' works: I show you a result of running a 'cat' command to 'pastebinit' :
```

sysop@1404mini:~$ cat /etc/default/grub | pastebinit
http://paste.ubuntu.com/11893588/
sysop@1404mini:~$ 

```
IF you  browse that " [http://paste.ubuntu.com/11893588/](http://paste.ubuntu.com/11893588/) " in your browser, you will see my grub config file.
Similarly we can see the results from your terminal commands: All we 'need' to be able to read are the numerics of the URL.

If your thoughts differ, I will entertain an alternate view .

[INDENT][INDENT][INDENT]we try and try again
[INDENT][INDENT][INDENT]see what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-17
nfidia; OH Yeah !

> 
Thanks for the link. So all this "Its Utopic" stuff are features from a newer Ubuntu release (14.10)?

Yes, you have the right of it. and to complicate our situation, 14.10's kernel is going End_Of_Life in a few days, and we MUST upgrade the kernel to that of 15.04 . Humm ... I wonder if it is available yet in the update-manager system ? Now that is another idea ! Maybe if we can upgrade the kernel - along with the supporting libraries and xserver , that process will fix our issue for us ???

[INDENT][INDENT][INDENT]could be
[/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-17
Good morning* Bashing-Om,

* I hope I correctly calculated the time zone difference between us. I am located in Germany. But I have nothing to do with our Minister of Finances, Dr. Schäuble, to say something politcally. He is currently hated by a lot of Greeks. I apologize for this.

> **Bashing-om said:**
> By the way, your command of the English language is admirable, you do well . English is the only language I am able to converse in, and sometimes not too well .

Thank you. Oh, I think your English is very good, I sometimes need to look up English words that you use. 

> I do not think it is possible to revert a system back from (H)ard(W)are (E)nablement. IF required to have and use the original kernel, we would have to (RE-)install and make sure the install is release 14.04[color=green].1[/color]. This so far as I know, perhaps others can advise if this is not the fact.

OK, thanks for the hint. Hm.

I think Ubuntu should stop implementing things that are too far away from general Linux standards.

> Presently, I think the focus of our attention is to get Xorg functional, and then be able to install the open source driver.

So you think it is of no importance that my problem also occurs even if I start my Ubuntu installation in text mode?

> With the situation of not able to see the complete outputs in terminal, let's get an alternate means to see and relay these outputs -> we use our paste site for this purpose:
```

sudo apt-get install pastebinit

```

I think, now, we want to know how the system responds and what the advise from the system is when we attempt to install that required dependency, xserver-xorg-core  .

Isn't the requred dependency that "abi" package?

> ```

sudo apt-get install xserver-xorg-core | pastebinit

```
The result from the package manager will be output to the pastebin site. The site will give you a URL back in terminal. Can you see enough of this URL to relay that URL back here to the thread ?
As an example of how 'pastebinit' works: I show you a result of running a 'cat' command to 'pastebinit' :
```

sysop@1404mini:~$ cat /etc/default/grub | pastebinit
http://paste.ubuntu.com/11893588/
sysop@1404mini:~$ 

```
IF you  browse that " [http://paste.ubuntu.com/11893588/](http://paste.ubuntu.com/11893588/) " in your browser, you will see my grub config file.
Similarly we can see the results from your terminal commands: All we 'need' to be able to read are the numerics of the URL.

I have installed the pastebinit programme and will now restart Ubuntu in text mode and execute the command "sudo apt-get install xserver-xorg-core | pastebinit"

Just a moment please ...

---

### Post by nfidia on 2015-07-17
> **Bashing-om said:**
> nfidia; OH Yeah !


Yes, you have the right of it. and to complicate our situation, 14.10's kernel is going End_Of_Life in a few days, and we MUST upgrade the kernel to that of 15.04 . Humm ... I wonder if it is available yet in the update-manager system ? Now that is another idea ! Maybe if we can upgrade the kernel - along with the supporting libraries and xserver , that process will fix our issue for us ???

[INDENT][INDENT][INDENT]could be
[/INDENT][/INDENT][/INDENT]

Yes, that could be. Let's see.

---

### Post by nfidia on 2015-07-17
During the last boot of my Ubuntu installation, I started Ubuntu in text mode. Then I typed in the command

```
sudo apt-get install xserver-xorg-core | pastebinit

```
, then I entered my password (blindly).

I expected that TTY1 would then present me a list of packages that would be removed by this command, and a list of packages that would be installed by this command.

But all this was not shown in TTY1. Instead I again saw a part of the prompt.

So this approach did not work.

So now I will execute this command in a terminal which I will open within GNOME. Because then I can see the full output of what the terminal returns to me.

But due to this I will remove and re-install X, and thus I will not see the result of that command in GNOME. So I will not be able to see the pastebinit URL. 

But I will try this because the command 

```
sudo apt-get install xserver-xorg-core
```

in such a terminal did not give me any information that such an (un-) installation cannot be done due to a missing package (the abi package).

So I will now execute the command 

```
sudo apt-get install xserver-xorg-core | pastebinit
```

in a terminal that I will open in the GNOME GUI.

See you later for a possible result.

---

### Post by nfidia on 2015-07-17
A feedback:

I just executed the command

```
sudo apt-get install xserver-xorg-core | pastebinit
```

in a terminal which I opened from within GNOME.

Result: Having typed in my password (blindly), the prompt hangs, no user input possible. I normally would need to enter a "Y" or a "n" to continue the execution of the command:

```
sudo apt-get install xserver-xorg-core
```

, but the pastebinit command does not allow me to enter a "Y" or a "n".

Bashing-om, I am sorry, but we cannot use the pastebinit command in connection with the command "apt-get install ...".

So now I will do a brutal execution of the command 

```
sudo apt-get install xserver-xorg-core
```

within a terminal that I opened within GNOME. Let's see what happens.

---

### Post by nfidia on 2015-07-17
Another feedback:

So I entered the command

```
sudo apt-get install xserver-xorg-core
```

in a terminal that I opened within GNOME. I then first typed in my password (blindly), and then I got the question 

> Do you want to continue? [Y/n]

I typed in "Y" (without quotation marks".

The result of this user input was the message "Abort".

Strange.

This is what I did:

> jrad@music:~/Schreibtisch$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gstreamer1.0-gnonlin
  kdenlive-data krita-data libakonadi-kde4 libakonadiprotocolinternals1
  libappindicator1 libastro1 libbonoboui2-0 libbonoboui2-common
  libboost-python1.54.0 libcauchy0.0 libcolord-gtk1 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libltc11
  liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data libmlt6
  libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-30-lowlatency linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  marble-data marble-plugins melt mencoder mypaint-data openshot-doc
  phatch-cli python-appindicator python-dateutil python-gnome2 python-gst-1.0
  python-hachoir-core python-hachoir-metadata python-hachoir-parser
  python-kaa-base python-kaa-metadata python-matplotlib python-matplotlib-data
  python-mlt python-pyexiv2 python-pyexiv2-doc python-pygoocanvas
  python-pyorbit python-pyparsing python-sqlite python-support python-tz
  rawtherapee-data transcode transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  xserver-xorg xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
Suggested packages:
  libglide3 xfonts-100dpi xfonts-75dpi gpointing-device-settings touchfreeze
  firmware-linux
The following packages will be REMOVED
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gtkclutter-1.0 gir1.2-totem-1.0
  gstreamer1.0-clutter libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15
  libegl1-mesa-drivers-lts-utopic libegl1-mesa-lts-utopic libgbm1-lts-utopic
  libgl1-mesa-dri-lts-utopic libgl1-mesa-glx-lts-utopic
  libglapi-mesa-lts-utopic libgles1-mesa-lts-utopic libgles2-mesa-lts-utopic
  libopenvg1-mesa-lts-utopic libtotem0 libwayland-egl1-mesa-lts-utopic
  libxatracker2-lts-utopic totem totem-mozilla totem-plugins
  xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic
  xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic
  xserver-xorg-input-synaptics-lts-utopic
  xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic
  xserver-xorg-lts-utopic xserver-xorg-video-cirrus-lts-utopic
  xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic
  xserver-xorg-video-mach64-lts-utopic
  xserver-xorg-video-mach64-lts-utopic-dbg xserver-xorg-video-mga-lts-utopic
  xserver-xorg-video-modesetting-lts-utopic
  xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic
  xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic
  xserver-xorg-video-r128-lts-utopic-dbg xserver-xorg-video-radeon-lts-utopic
  xserver-xorg-video-radeon-lts-utopic-dbg
  xserver-xorg-video-savage-lts-utopic
  xserver-xorg-video-siliconmotion-lts-utopic
  xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic
  xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic
  xserver-xorg-video-vmware-lts-utopic
The following NEW packages will be installed
  libegl1-mesa libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-glamoregl
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa
0 to upgrade, 35 to newly install, 56 to remove and 1 not to upgrade.
Need to get 8.210 kB of archives.
After this operation, 6.268 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.
jrad@music:~/Schreibtisch$

I will now try this command in TTY1 after a reboot of Ubuntu in text mode. Maybe then I do not get an "Abort" message. Because I guess that this message could have been caused because I wanted to un- and re-install X within a running X environment.

---

### Post by nfidia on 2015-07-17
Hi Bashing-om, another feedback:

I just started a TTY1 in Ubuntu by having started Ubuntu in text mode. I then entered the command

```
apt-get install xserver-xorg-core
```

, then my password (blindly), then I expected a list of packages to be displayed that would be removed and installed by this command. 

But I did not see such a list. I did not see any output in TTY1.

Nevertheless I entered "Y", but nothing happened.

I repeated these steps three times, but I always had the same results in TTY1 as descibed above in this post.

Hm.

---

### Post by Bashing-om on 2015-07-17
nfidia; Welp;

I am guilty of not think'n things through if I Were in this situation. You are correct in that a '(y)es' input to 'apt-get install' is required - I had not thought of that . There is a flag for that condition:
```

sudo apt-get install -y <package>

```

Anyway, as things are not working out to well as it is ... Let's try :
```

sudo apt-get autoremove

```
and let the package manager gut the X layer.

Now, lets see what it will take to put the system back together .
Let's look at the package manager's "fix broken packages" application:
```

sudo apt-get -f install
sudo dpkg -C

```
Realizing that we are most likely going to have to give the package manager a helping hand in removing the current xserver and installing afresh .

[INDENT][INDENT]right wrong or otherwise
[INDENT][INDENT][INDENT]do something -> more info 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-17
Hey Bashing-Om,

You are not guilty of anything. I am happy that there is somebody who tries to help me ;)

So this is the latest feedback:

1. I started a TTY1 (I started Ubuntu in text mode) and entered the command

```
sudo apt-get install -y xserver-xorg-core | pastebinit
```

=> nothing happend. No output in TTY1

2. I entered the command:

```
sudo apt-get autoremove
```

=> nothing happend. No output in TTY1

3., I did not apply

```
sudo dpkg -C
```

4.. I started Ubuntu normally, then I opened a terminal within GNOME and entered the command:

```
sudo apt-get install -y xserver-xorg-core
```

This time there was no "abort" message, but instead, as I could follow the output in the terninal, first the "Its-utopic" packages and other packages were removed, and then the normal xserver packages were installed.

5. I applied a reboot.

4. The problem (display area out of alignment) still exits.

Best regards,

nfidia/radeonot

---

### Post by Bashing-om on 2015-07-17
nfidia; Well.

Progress !
With out being able to see those outputs, I can only hazard - in the full meaning of that word -  a guess that the open source driver is still to be installed. That no graphics driver for the GUI is available.
once more let's run the purge/install routine:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```

IF the system reports errors, I really need to see that output.

In the event that all does go well this time. Reboot and let's see what the result is. Still bad we start looking at the log files to see where the failure lies and also what the package manager relates .

This is a beautiful system, if one knows where to look it tells you what is ailing it .

EDIT: In respect to 'pastebinit'
The only result when piping to 'pastebinit' is a URL returned to terminal . I had hoped that is the case here ?

EDIT #2 !
I bet it would behoove us greatly to make sure the system is updated ! Before the above run these terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```then see if we can purge/re-install the graphics driver ,

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-18
Hi Bashing-om,

> **Bashing-om said:**
> 
With out being able to see those outputs, I can only hazard - in the full meaning of that word -  a guess that the open source driver is still to be installed. That no graphics driver for the GUI is available.

My fault. I did not make a "protocol" about what happened when I executed the command:

```
sudo apt-get install -y xserver-xorg-core
```

But now I will do that for every command that you specified in your last post:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

=> 

> jrad@music:~/Schreibtisch$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[sudo] password for jrad: 
mv: cannot stat ‘/etc/X11/xorg.conf’: No such file or directory
jrad@music:~/Schreibtisch$

```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```

=> 

> jrad@music:~/Schreibtisch$ sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
jrad@music:~/Schreibtisch$

```
sudo apt-get install dkms
```

=>

> jrad@music:~/Schreibtisch$ sudo apt-get install dkms
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
Suggested packages:
  dpkg-dev debhelper
The following packages will be upgraded:
  dkms
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 64,6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04.1 [64,6 kB]
Fetched 64,6 kB in 0s (161 kB/s)
(Reading database ... 331752 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1) over (2.2.0.3-1.1ubuntu5.14.04) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
jrad@music:~/Schreibtisch$

```
sudo apt-get install xserver-xorg-video-radeon
```

=>

> jrad@music:~/Schreibtisch$ sudo apt-get install xserver-xorg-video-radeon
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-radeon is already the newest version.
xserver-xorg-video-radeon set to manually installed.
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
jrad@music:~/Schreibtisch$

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

=>

> jrad@music:~/Schreibtisch$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 3 reinstalled, 0 to remove and 0 not to upgrade.
Need to get 0 B/6.059 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 331752 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.4_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.4) over (10.1.3-0ubuntu0.4) ...
Preparing to unpack .../xserver-xorg-core_2%3a1.15.1-0ubuntu2.7_i386.deb ...
Unpacking xserver-xorg-core (2:1.15.1-0ubuntu2.7) over (2:1.15.1-0ubuntu2.7) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.4_i386.deb ...
Unpacking libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4) over (10.1.3-0ubuntu0.4) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.4) ...
Setting up libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4) ...
Setting up xserver-xorg-core (2:1.15.1-0ubuntu2.7) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
jrad@music:~/Schreibtisch$

```
sudo dpkg-reconfigure xserver-xorg
```

=>

> jrad@music:~/Schreibtisch$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for jrad: 
jrad@music:~/Schreibtisch$ 


```
sudo update-initramfs -u
```

=>

> jrad@music:~/Schreibtisch$ sudo update-initramfs -u
[sudo] password for jrad: 
update-initramfs: Generating /boot/initrd.img-3.16.0-43-lowlatency
jrad@music:~/Schreibtisch$

> IF the system reports errors, I really need to see that output.

I could not see any errors so far. The radeon driver was already installed.

I will now do a reboot, and will report here about the result.

> Still bad we start looking at the log files to see where the failure lies and also what the package manager relates .

This is a beautiful system, if one knows where to look it tells you what is ailing it 

Wouldn't a simple "dmesg" help here, at least a bit?

> EDIT: In respect to 'pastebinit'
The only result when piping to 'pastebinit' is a URL returned to terminal . I had hoped that is the case here ?

Sorry, I do not know what you mean. When I executed commands together with the pastebinit command, I never got an URL turned back in a GNOME-based terminal or in TTY1.

> EDIT #2 !
I bet it would behoove us greatly to make sure the system is updated ! Before the above run these terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```then see if we can purge/re-install the graphics driver ,

Oops. It's too late, I executed the above-mentioned commands (the command in the beginning of your last post) already, but did not apply a reboot yet. After the reboot, if it appears that my problem still exists, I will first do that update stuff and then I again will apply the command that you specified in the beginning of your last post.

After the dist-upgrade i will tell you the installed kernel version via the command uname -a

---

### Post by nfidia on 2015-07-18
I applied a reboot: no effect. Problem still exists.

This is the currently installed kernel:

> jrad@music:~/Schreibtisch$ uname -a
Linux music 3.16.0-43-lowlatency #58~14.04.1-Ubuntu SMP PREEMPT Mon Jun 22 10:48:48 UTC 2015 i686 athlon i686 GNU/Linux
jrad@music:~/Schreibtisch$

I will now do a dist-upgrade by executing the commands which you specified in your last post. I will not make any protocols about this because I guess that no (relevant) errors will take place during this process.

---

### Post by nfidia on 2015-07-18
I just executed the commands:

> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

My machine has not been modified by these commands. Here is the output of the command "sudo apt-get dist-upgrade":

> jrad@music:~/Schreibtisch$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
jrad@music:~/Schreibtisch$ 


---

### Post by Bashing-om on 2015-07-18
nfidia; Hey ;

Does not look too shabby ( american slang expression) . The package manager accepted all directives with no complaints. I do believe we made further progress as now :
> 
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

we no longer have the "need to upgrade" 1 package advisory. And I do think at this point we "should" - breath held :
```

sudo apt-get autoremove

```
due to the system's advisory:
> 
The following packages were automatically installed and are no longer required:
<snip>
Use 'apt-get autoremove' to remove them.

With the amount of orphaned packages that the system perceives when we do this, I can accept there will be unexpected breakage. However, I do think we should heed the advise and do what we can to clean up the system before proceeding .

Looking at 'dmesg' is always a good idea for system wide reporting, but, the more relevant/direct reports are in the files:
```

less /var/log/Xorg.0.log
less .xsession-errors

```

So for now, I do suggest we run the 'autoremove' command and then reboot the system - breath held .
Once back up, let's check the package manager status:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C
---------------------------
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

And take a look at the log files, see what the system reports . IF the system comes up and no other problems other than the resolution, then I do consider that the TV display does not export the resolution data, and we can then take matters into our own hands and direct the kernel to use a particular resolution.

Maybe at this point stability has been achieved
[INDENT][INDENT][INDENT]we can talk to the kernel
[/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-18
Hey Bashing-om

this is the output of the autoremove command:

```
jrad@music:~/Schreibtisch$ sudo apt-get autoremove
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  calligra-data calligra-libs dcraw dvdisaster dvdisaster-doc dvdstyler-data
  dvgrab exiftran ffmpegthumbnailer fontforge-common gir1.2-ges-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-json-1.0 gir1.2-totem-plparser-1.0
  gstreamer1.0-gnonlin kdenlive-data krita-data libakonadi-kde4
  libakonadiprotocolinternals1 libappindicator1 libastro1 libbonoboui2-0
  libbonoboui2-common libboost-python1.54.0 libcauchy0.0 libclutter-1.0-common
  libcogl-common libcolord-gtk1 libepoxy0 libevdev2 libffmpegthumbnailer4
  libflickcurl0 libfontforge1 libgdraw4 libges-1.0-0 libgnomeui-0
  libgnomeui-common libgoocanvas-common libgoocanvas3 libgps20
  libgraphicsmagick3 libgstreamermm-0.10-2 libhyphen0 libicc2
  libimage-exiftool-perl libimdi0 libimlib2 libindicator7 libiptcdata0
  libiso9660-8 libjs-prototype libjs-scriptaculous libkabc4 libkcalcore4
  libkdcraw-data libkdcraw23 libkldap4 libkresources4 libkrossui4 libllvm3.5
  libltc11 liblua5.2-0 libm2mml0.0 libmarblewidget18 libmlt++3 libmlt-data
  libmlt6 libmpcdec6 liboggkate1 libphononexperimental4 libpodofo0.9.0
  libqextserialport1 libqtlocation1 libquazip0 libshp1 libspiro0 libsqlite0
  libsubtitleeditor0 libuninameslist0 libva-glx1 libva-x11-1 libvcdinfo0
  libwlocate0 libwxsvg0 libxcb-xv0 libxine2 libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins libxine2-x
  linux-generic-lts-utopic linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-30-lowlatency
  linux-headers-generic-lts-utopic linux-image-3.16.0-30-generic
  linux-image-3.16.0-30-lowlatency linux-image-extra-3.16.0-30-generic
  linux-image-generic-lts-utopic marble-data marble-plugins melt mencoder
  mypaint-data openshot-doc phatch-cli python-appindicator python-dateutil
  python-gnome2 python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-kaa-base python-kaa-metadata python-matplotlib
  python-matplotlib-data python-mlt python-pyexiv2 python-pyexiv2-doc
  python-pygoocanvas python-pyorbit python-pyparsing python-sqlite
  python-support python-tz rawtherapee-data totem-common transcode
  transcode-doc twolame xcftools xine-ui
0 to upgrade, 0 to newly install, 135 to remove and 0 not to upgrade.
After this operation, 756 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 331751 files and directories currently installed.)
Removing calligra-libs (1:2.8.1-1-0ubuntu3) ...
Removing calligra-data (1:2.8.1-1-0ubuntu3) ...
Removing dcraw (9.19-1.1ubuntu1) ...
Removing dvdisaster (0.72.4-1) ...
Removing dvdisaster-doc (0.72.4-1) ...
Removing dvdstyler-data (2.5.2-0ubuntu3) ...
Removing dvgrab (3.5-2) ...
Removing exiftran (2.07-11) ...
Removing ffmpegthumbnailer (2.0.8-2) ...
Removing fontforge-common (20120731.b-5) ...
Removing gir1.2-ges-1.0 (1.2.0-2) ...
Removing gir1.2-gst-plugins-base-1.0 (1.2.4-1~ubuntu1) ...
Removing gir1.2-json-1.0 (0.16.2-1ubuntu1) ...
Removing gir1.2-totem-plparser-1.0 (3.10.2-0ubuntu1) ...
Removing libges-1.0-0 (1.2.0-2) ...
Removing gstreamer1.0-gnonlin (1.2.0-1) ...
Removing kdenlive-data (0.9.6-5ubuntu1) ...
Removing krita-data (1:2.8.1-1-0ubuntu3) ...
Removing libakonadi-kde4 (4:4.13.3-0ubuntu0.2) ...
Removing libakonadiprotocolinternals1 (1.12.1-0ubuntu1.1) ...
Removing python-appindicator (12.10.1+13.10.20130920-0ubuntu4.1) ...
Removing libappindicator1 (12.10.1+13.10.20130920-0ubuntu4.1) ...
Removing marble-plugins (4:4.13.3-0ubuntu0.1) ...
Removing libmarblewidget18 (4:4.13.3-0ubuntu0.1) ...
Removing libastro1 (4:4.13.3-0ubuntu0.1) ...
Removing python-gnome2 (2.28.1+dfsg-1ubuntu2) ...
Removing libgnomeui-0:i386 (2.24.5-3) ...
Removing libbonoboui2-0:i386 (2.24.5-0ubuntu3) ...
Removing libbonoboui2-common (2.24.5-0ubuntu3) ...
Removing phatch-cli (0.2.7.1-3) ...
Removing python-pyexiv2 (0.3.2-5ubuntu3) ...
Removing libboost-python1.54.0:i386 (1.54.0-4ubuntu3.1) ...
Removing libm2mml0.0 (0.9.0-0ubuntu1) ...
Removing libcauchy0.0 (0.9.0-0ubuntu1) ...
Removing libclutter-1.0-common (1.16.4-0ubuntu2) ...
Removing libcogl-common (1.16.2-1) ...
Removing libcolord-gtk1:i386 (0.1.25-1.1) ...
Removing libepoxy0 (1.1-1build1) ...
Removing libevdev2 (1.0.99.2+dfsg-2ubuntu2) ...
Removing libffmpegthumbnailer4 (2.0.8-2) ...
Removing libflickcurl0:i386 (1.25-1ubuntu1) ...
Removing libgdraw4 (20120731.b-5) ...
Removing libfontforge1 (20120731.b-5) ...
Removing libgnomeui-common (2.24.5-3) ...
Removing python-pygoocanvas (0.14.1-1ubuntu8) ...
Removing libgoocanvas3 (0.15-1.1ubuntu1) ...
Removing libgoocanvas-common (0.15-1.1ubuntu1) ...
Removing libgps20:i386 (3.9-3) ...
Removing xine-ui (0.99.7-1) ...
Removing libxine2 (1.2.4-2ubuntu1) ...
Removing libxine2-plugins (1.2.4-2ubuntu1) ...
Removing libxine2-misc-plugins (1.2.4-2ubuntu1) ...
Removing libgraphicsmagick3 (1.3.18-1ubuntu3) ...
Removing libsubtitleeditor0:i386 (0.41.0-2ubuntu1) ...
Removing libgstreamermm-0.10-2 (0.10.11-0ubuntu2) ...
Removing libhyphen0 (2.8.6-3ubuntu2) ...
Removing libicc2:i386 (2.12+argyll1.5.1-5ubuntu1) ...
Removing libimage-exiftool-perl (9.46-1) ...
Removing libimdi0:i386 (1.5.1-5ubuntu1) ...
Removing libimlib2 (1.4.6-2) ...
Removing libindicator7 (12.10.2+14.04.20141007.1-0ubuntu1) ...
Removing libiptcdata0 (1.0.4-3ubuntu3) ...
Removing libvcdinfo0 (0.7.24+dfsg-0.1ubuntu2) ...
Removing libiso9660-8 (0.83-4.1ubuntu1) ...
Removing libjs-scriptaculous (1.9.0-2) ...
Removing libjs-prototype (1.7.1-3) ...
Removing libkabc4 (4:4.13.3-0ubuntu0.2) ...
Removing libkcalcore4 (4:4.13.3-0ubuntu0.2) ...
Removing libkdcraw23 (4:4.13.0-0ubuntu1) ...
Removing libkdcraw-data (4:4.13.0-0ubuntu1) ...
Removing libkldap4 (4:4.13.3-0ubuntu0.2) ...
Removing libkresources4 (4:4.13.3-0ubuntu0.2) ...
Removing libkrossui4 (4:4.13.3-0ubuntu0.2) ...
Removing libllvm3.5:i386 (1:3.5-4ubuntu2~trusty2) ...
Removing libltc11:i386 (1.1.3-1) ...
Removing liblua5.2-0:i386 (5.2.3-1) ...
Removing python-mlt (0.9.0-3) ...
Removing libmlt++3 (0.9.0-3) ...
Removing melt (0.9.0-3) ...
Removing libmlt-data (0.9.0-3) ...
Removing libmlt6 (0.9.0-3) ...
Removing libmpcdec6 (2:0.1~r459-1ubuntu3) ...
Removing liboggkate1 (0.4.1-1ubuntu1) ...
Removing libphononexperimental4:i386 (4:4.7.80-0ubuntu1~ubuntu14.04) ...
Removing libpodofo0.9.0 (0.9.0-1.2) ...
Removing libqextserialport1:i386 (1.2.0~rc1+git7-g3be3fbf-1) ...
Removing libqtlocation1:i386 (1.2.0-3ubuntu5) ...
Removing libquazip0:i386 (0.6.2-0ubuntu1) ...
Removing libshp1:i386 (1.2.10-7) ...
Removing libspiro0:i386 (20071029-8ubuntu1) ...
Removing python-kaa-metadata (0.7.7+svn4596-4) ...
Removing python-kaa-base (0.6.0+svn4596-1) ...
Removing python-sqlite (1.0.1-11) ...
Removing libsqlite0 (2.8.17-10ubuntu2) ...
Removing libuninameslist0 (0.3.20130501-3) ...
Removing libxine2-x (1.2.4-2ubuntu1) ...
Removing libva-glx1:i386 (1.3.0-2) ...
Removing libva-x11-1:i386 (1.3.0-2) ...
Removing libwlocate0 (0.0git20130108-0ubuntu1) ...
Removing libwxsvg0:i386 (2:1.2~dfsg0-1ubuntu1) ...
Removing libxcb-xv0:i386 (1.10-2ubuntu1) ...
Removing libxine2-ffmpeg (1.2.4-2ubuntu1) ...
Removing libxine2-bin (1.2.4-2ubuntu1) ...
Removing libxine2-doc (1.2.4-2ubuntu1) ...
Removing linux-generic-lts-utopic (3.16.0.43.34) ...
Removing linux-headers-3.16.0-30-lowlatency (3.16.0-30.40~14.04.1) ...
Removing linux-headers-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Removing linux-headers-3.16.0-30 (3.16.0-30.40~14.04.1) ...
Removing linux-headers-generic-lts-utopic (3.16.0.43.34) ...
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-generic
Found initrd image: /boot/initrd.img-3.16.0-43-generic
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found linux image: /boot/vmlinuz-3.16.0-30-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-30-lowlatency
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Debian GNU/Linux (7.8) on /dev/sda2
done
Removing linux-image-3.16.0-30-generic (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-generic
Found initrd image: /boot/initrd.img-3.16.0-43-generic
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found linux image: /boot/vmlinuz-3.16.0-30-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-30-lowlatency
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Debian GNU/Linux (7.8) on /dev/sda2
done
Removing linux-image-3.16.0-30-lowlatency (3.16.0-30.40~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.16.0-30-lowlatency /boot/vmlinuz-3.16.0-30-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-lowlatency /boot/vmlinuz-3.16.0-30-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.16.0-30-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-lowlatency /boot/vmlinuz-3.16.0-30-lowlatency
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-43-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-43-generic
Found initrd image: /boot/initrd.img-3.16.0-43-generic
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Debian GNU/Linux (7.8) on /dev/sda2
done
Removing linux-image-generic-lts-utopic (3.16.0.43.34) ...
Removing marble-data (4:4.13.3-0ubuntu0.1) ...
Removing mencoder (2:1.1+dfsg1-0ubuntu3) ...
Removing mypaint-data (1.1.0-3) ...
Removing openshot-doc (1.4.3-1.1) ...
Removing python-matplotlib (1.3.1-1ubuntu5) ...
Removing python-dateutil (1.5+dfsg-1ubuntu1) ...
Removing python-gst-1.0 (1.2.0-1) ...
Removing python-hachoir-metadata (1.3.3-1) ...
Removing python-hachoir-parser (1.3.4-1) ...
Removing python-hachoir-core (1.3.3-3) ...
Removing python-matplotlib-data (1.3.1-1ubuntu5) ...
Removing python-pyexiv2-doc (0.3.2-5ubuntu3) ...
Removing python-pyorbit (2.24.0-6ubuntu4) ...
Removing python-pyparsing (2.0.1+dfsg1-1build1) ...
Removing python-support (1.0.15) ...
Removing python-tz (2012c-1build1) ...
Removing rawtherapee-data (4.0.12+dfsg-2) ...
Removing totem-common (3.10.1-1ubuntu4) ...
Removing transcode (3:1.1.7-8) ...
Removing transcode-doc (3:1.1.7-8) ...
Removing twolame (0.3.13-1ubuntu1) ...
Removing xcftools (1.0.7-4ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 removed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
jrad@music:~/Schreibtisch$
```

I will now do a reboot and proceed with what you wrote in your last post,

Best regards,

nfidia

---

### Post by nfidia on 2015-07-18
Hi Bashing-om,

I am back, system rebooted. No change with regards to the behaviour, by the way.

Now I will apply these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C
---------------------------
lspci -vnn | grep VGA -A 12
sudo lshw -C display
```

1, Result of "sudo apt-get update":

> jrad@music:~/Schreibtisch$ sudo apt-get update
[sudo] password for jrad: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en   
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty InRelease                              
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release.gpg                            
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release                                
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates Release [63,5 kB]            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports Release                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Sources                           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/main Translation-de                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/multiverse Translation-de              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/restricted Translation-de              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty/universe Translation-de                
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Sources [215 kB]        
Get:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Sources [3.433 B] 
Get:5 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Sources [125 kB]    
Get:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Sources [5.138 B] 
Get:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main i386 Packages [555 kB]  
Get:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted i386 Packages [11,8 kB]
Get:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe i386 Packages [296 kB]
Get:10 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12,1 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/multiverse Translation-en 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports/universe Translation-en      
Fetched 1.288 kB in 19s (66,6 kB/s)                                            
Reading package lists... Done
jrad@music:~/Schreibtisch$

2. Result of "sudo apt-get upgrade":

> jrad@music:~/Schreibtisch$ sudo apt-get upgrade
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
jrad@music:~/Schreibtisch$

3. Result of "sudo apt-get -f install":

> jrad@music:~/Schreibtisch$ sudo apt-get -f install
[sudo] password for jrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
jrad@music:~/Schreibtisch$

4. Result of "sudo dpkg -C"

> jrad@music:~/Schreibtisch$ sudo dpkg -C
[sudo] password for jrad: 
jrad@music:~/Schreibtisch$

5. Result of "lspci -vnn | grep VGA -A 12":

> jrad@music:~/Schreibtisch$ sudo dpkg -C
[sudo] password for jrad: 
jrad@music:~/Schreibtisch$ lspci -vnn | grep VGA -A 12
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at fe028000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1612]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:aa38]
	Flags: bus master, fast devsel, latency 0, IRQ 44
jrad@music:~/Schreibtisch$ 


6. Result of "sudo lshw -C display":

> jrad@music:~/Schreibtisch$ sudo lshw -C display
[sudo] password for jrad: 
  *-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fdee0000-fdeeffff ioport:ee00(size=256) memory:fde00000-fde1ffff
jrad@music:~/Schreibtisch$

---

### Post by Bashing-om on 2015-07-18
nfidia; Bated breath.

I do not know what to make of:
> 
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...

Does not seem at this time to be of great import, so we proceed and 
I await the results of the reboot/updates.

[INDENT][INDENT]overall, look'n good
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-18
Hi Bashing-om,

Now I will apply these commands:

```
less /var/log/Xorg.0.log
less .xsession-errors
```

Doesn't work with regards to copying the contents of these files, I will use gedit instead:

1. Content of  /var/log/Xorg.0.log:

```
[    31.142] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    31.142] X Protocol Version 11, Revision 0
[    31.142] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[    31.142] Current Operating System: Linux music 3.16.0-43-lowlatency #58~14.04.1-Ubuntu SMP PREEMPT Mon Jun 22 10:48:48 UTC 2015 i686
[    31.142] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-43-lowlatency root=UUID=92d39ae9-9e50-4e0e-83c5-64097cd15fd3 ro quiet splash vt.handoff=7
[    31.142] Build Date: 12 February 2015  02:49:46PM
[    31.142] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    31.142] Current version of pixman: 0.30.2
[    31.142] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    31.142] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.142] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 18 20:17:28 2015
[    31.178] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.225] (==) No Layout section.  Using the first Screen section.
[    31.225] (==) No screen section available. Using defaults.
[    31.225] (**) |-->Screen "Default Screen Section" (0)
[    31.225] (**) |   |-->Monitor "<default monitor>"
[    31.237] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    31.237] (==) Automatically adding devices
[    31.237] (==) Automatically enabling devices
[    31.237] (==) Automatically adding GPU devices
[    31.269] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.269] 	Entry deleted from font path.
[    31.269] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.269] 	Entry deleted from font path.
[    31.269] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.269] 	Entry deleted from font path.
[    31.269] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.269] 	Entry deleted from font path.
[    31.269] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.269] 	Entry deleted from font path.
[    31.269] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    31.269] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.269] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.269] (II) Loader magic: 0xb771f6c0
[    31.269] (II) Module ABI versions:
[    31.269] 	X.Org ANSI C Emulation: 0.4
[    31.269] 	X.Org Video Driver: 15.0
[    31.269] 	X.Org XInput driver : 20.0
[    31.269] 	X.Org Server Extension : 8.0
[    31.270] (II) xfree86: Adding drm device (/dev/dri/card0)
[    31.271] (--) PCI:*(0:1:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    31.301] Initializing built-in extension Generic Event Extension
[    31.301] Initializing built-in extension SHAPE
[    31.301] Initializing built-in extension MIT-SHM
[    31.301] Initializing built-in extension XInputExtension
[    31.301] Initializing built-in extension XTEST
[    31.301] Initializing built-in extension BIG-REQUESTS
[    31.301] Initializing built-in extension SYNC
[    31.301] Initializing built-in extension XKEYBOARD
[    31.301] Initializing built-in extension XC-MISC
[    31.301] Initializing built-in extension SECURITY
[    31.301] Initializing built-in extension XINERAMA
[    31.301] Initializing built-in extension XFIXES
[    31.301] Initializing built-in extension RENDER
[    31.301] Initializing built-in extension RANDR
[    31.301] Initializing built-in extension COMPOSITE
[    31.301] Initializing built-in extension DAMAGE
[    31.301] Initializing built-in extension MIT-SCREEN-SAVER
[    31.301] Initializing built-in extension DOUBLE-BUFFER
[    31.301] Initializing built-in extension RECORD
[    31.301] Initializing built-in extension DPMS
[    31.301] Initializing built-in extension Present
[    31.301] Initializing built-in extension DRI3
[    31.301] Initializing built-in extension X-Resource
[    31.301] Initializing built-in extension XVideo
[    31.301] Initializing built-in extension XVideo-MotionCompensation
[    31.301] Initializing built-in extension SELinux
[    31.301] Initializing built-in extension XFree86-VidModeExtension
[    31.301] Initializing built-in extension XFree86-DGA
[    31.301] Initializing built-in extension XFree86-DRI
[    31.301] Initializing built-in extension DRI2
[    31.301] (II) LoadModule: "glx"
[    31.335] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.642] (II) Module glx: vendor="X.Org Foundation"
[    31.642] 	compiled for 1.15.1, module version = 1.0.0
[    31.642] 	ABI class: X.Org Server Extension, version 8.0
[    31.642] (==) AIGLX enabled
[    31.642] Loading extension GLX
[    31.642] (==) Matched fglrx as autoconfigured driver 0
[    31.642] (==) Matched ati as autoconfigured driver 1
[    31.642] (==) Matched fglrx as autoconfigured driver 2
[    31.642] (==) Matched ati as autoconfigured driver 3
[    31.642] (==) Matched modesetting as autoconfigured driver 4
[    31.642] (==) Matched fbdev as autoconfigured driver 5
[    31.642] (==) Matched vesa as autoconfigured driver 6
[    31.642] (==) Assigned the driver to the xf86ConfigLayout
[    31.642] (II) LoadModule: "fglrx"
[    31.671] (WW) Warning, couldn't open module fglrx
[    31.671] (II) UnloadModule: "fglrx"
[    31.671] (II) Unloading fglrx
[    31.671] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    31.671] (II) LoadModule: "ati"
[    31.671] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    31.684] (II) Module ati: vendor="X.Org Foundation"
[    31.684] 	compiled for 1.15.1, module version = 7.3.0
[    31.684] 	Module class: X.Org Video Driver
[    31.684] 	ABI class: X.Org Video Driver, version 15.0
[    31.684] (II) LoadModule: "radeon"
[    31.684] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    31.950] (II) Module radeon: vendor="X.Org Foundation"
[    31.951] 	compiled for 1.15.1, module version = 7.3.0
[    31.951] 	Module class: X.Org Video Driver
[    31.951] 	ABI class: X.Org Video Driver, version 15.0
[    31.951] (II) LoadModule: "modesetting"
[    31.951] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.971] (II) Module modesetting: vendor="X.Org Foundation"
[    31.971] 	compiled for 1.15.0, module version = 0.8.1
[    31.971] 	Module class: X.Org Video Driver
[    31.971] 	ABI class: X.Org Video Driver, version 15.0
[    31.971] (II) LoadModule: "fbdev"
[    31.971] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.972] (II) Module fbdev: vendor="X.Org Foundation"
[    31.972] 	compiled for 1.15.0, module version = 0.4.4
[    31.972] 	Module class: X.Org Video Driver
[    31.972] 	ABI class: X.Org Video Driver, version 15.0
[    31.972] (II) LoadModule: "vesa"
[    31.972] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.973] (II) Module vesa: vendor="X.Org Foundation"
[    31.973] 	compiled for 1.15.0, module version = 2.3.3
[    31.973] 	Module class: X.Org Video Driver
[    31.973] 	ABI class: X.Org Video Driver, version 15.0
[    31.973] (==) Matched fglrx as autoconfigured driver 0
[    31.973] (==) Matched ati as autoconfigured driver 1
[    31.973] (==) Matched fglrx as autoconfigured driver 2
[    31.973] (==) Matched ati as autoconfigured driver 3
[    31.973] (==) Matched modesetting as autoconfigured driver 4
[    31.973] (==) Matched fbdev as autoconfigured driver 5
[    31.973] (==) Matched vesa as autoconfigured driver 6
[    31.973] (==) Assigned the driver to the xf86ConfigLayout
[    31.973] (II) LoadModule: "fglrx"
[    31.973] (WW) Warning, couldn't open module fglrx
[    31.973] (II) UnloadModule: "fglrx"
[    31.973] (II) Unloading fglrx
[    31.973] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    31.973] (II) LoadModule: "ati"
[    31.974] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    31.974] (II) Module ati: vendor="X.Org Foundation"
[    31.974] 	compiled for 1.15.1, module version = 7.3.0
[    31.974] 	Module class: X.Org Video Driver
[    31.974] 	ABI class: X.Org Video Driver, version 15.0
[    31.974] (II) LoadModule: "modesetting"
[    31.974] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.974] (II) Module modesetting: vendor="X.Org Foundation"
[    31.974] 	compiled for 1.15.0, module version = 0.8.1
[    31.974] 	Module class: X.Org Video Driver
[    31.974] 	ABI class: X.Org Video Driver, version 15.0
[    31.974] (II) UnloadModule: "modesetting"
[    31.974] (II) Unloading modesetting
[    31.974] (II) Failed to load module "modesetting" (already loaded, 0)
[    31.974] (II) LoadModule: "fbdev"
[    31.974] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.974] (II) Module fbdev: vendor="X.Org Foundation"
[    31.974] 	compiled for 1.15.0, module version = 0.4.4
[    31.974] 	Module class: X.Org Video Driver
[    31.974] 	ABI class: X.Org Video Driver, version 15.0
[    31.974] (II) UnloadModule: "fbdev"
[    31.974] (II) Unloading fbdev
[    31.974] (II) Failed to load module "fbdev" (already loaded, 0)
[    31.974] (II) LoadModule: "vesa"
[    31.974] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.974] (II) Module vesa: vendor="X.Org Foundation"
[    31.974] 	compiled for 1.15.0, module version = 2.3.3
[    31.974] 	Module class: X.Org Video Driver
[    31.974] 	ABI class: X.Org Video Driver, version 15.0
[    31.975] (II) UnloadModule: "vesa"
[    31.975] (II) Unloading vesa
[    31.975] (II) Failed to load module "vesa" (already loaded, 0)
[    31.975] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII
[    31.982] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    31.982] (II) FBDEV: driver for framebuffer: fbdev
[    31.982] (II) VESA: driver for VESA chipsets: vesa
[    31.982] (++) using VT number 7

[    31.996] (II) [KMS] Kernel modesetting enabled.
[    31.996] (WW) Falling back to old probe method for modesetting
[    31.996] (WW) Falling back to old probe method for fbdev
[    31.996] (II) Loading sub module "fbdevhw"
[    31.996] (II) LoadModule: "fbdevhw"
[    31.997] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.015] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.015] 	compiled for 1.15.1, module version = 0.0.2
[    32.015] 	ABI class: X.Org Video Driver, version 15.0
[    32.015] (WW) Falling back to old probe method for vesa
[    32.015] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    32.015] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    32.015] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    32.015] (==) RADEON(0): Default visual is TrueColor
[    32.015] (==) RADEON(0): RGB weight 888
[    32.015] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    32.015] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[    32.015] (II) Loading sub module "dri2"
[    32.015] (II) LoadModule: "dri2"
[    32.015] (II) Module "dri2" already built-in
[    32.015] (II) Loading sub module "exa"
[    32.015] (II) LoadModule: "exa"
[    32.016] (II) Loading /usr/lib/xorg/modules/libexa.so
[    32.055] (II) Module exa: vendor="X.Org Foundation"
[    32.055] 	compiled for 1.15.1, module version = 2.6.0
[    32.055] 	ABI class: X.Org Video Driver, version 15.0
[    32.055] (II) RADEON(0): KMS Color Tiling: enabled
[    32.055] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    32.055] (II) RADEON(0): KMS Pageflipping: enabled
[    32.055] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    32.089] (II) RADEON(0): Output VGA-0 has no monitor section
[    32.103] (II) RADEON(0): Output DVI-0 has no monitor section
[    32.137] (II) RADEON(0): EDID for output VGA-0
[    32.137] (II) RADEON(0): Manufacturer: PHL  Model: 0  Serial#: 16843009
[    32.137] (II) RADEON(0): Year: 2011  Week: 0
[    32.137] (II) RADEON(0): EDID Version: 1.3
[    32.137] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    32.137] (II) RADEON(0): Sync:  Separate
[    32.137] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 36
[    32.137] (II) RADEON(0): Gamma: 2.20
[    32.137] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    32.137] (II) RADEON(0): First detailed timing is preferred mode
[    32.137] (II) RADEON(0): redX: 0.646 redY: 0.334   greenX: 0.303 greenY: 0.616
[    32.137] (II) RADEON(0): blueX: 0.147 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[    32.137] (II) RADEON(0): Supported established timings:
[    32.137] (II) RADEON(0): 640x480@60Hz
[    32.137] (II) RADEON(0): 800x600@60Hz
[    32.137] (II) RADEON(0): 1024x768@60Hz
[    32.137] (II) RADEON(0): Manufacturer's mask: 0
[    32.137] (II) RADEON(0): Supported standard timings:
[    32.137] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    32.137] (II) RADEON(0): Supported detailed timing:
[    32.137] (II) RADEON(0): clock: 138.5 MHz   Image Size:  640 x 360 mm
[    32.138] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    32.138] (II) RADEON(0): v_active: 1080  v_sync: 1082  v_sync_end 1087 v_blanking: 1111 v_border: 0
[    32.138] (II) RADEON(0): Supported detailed timing:
[    32.138] (II) RADEON(0): clock: 84.8 MHz   Image Size:  640 x 360 mm
[    32.138] (II) RADEON(0): h_active: 1360  h_sync: 1432  h_sync_end 1568 h_blank_end 1776 h_border: 0
[    32.138] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 798 v_border: 0
[    32.138] (II) RADEON(0): Monitor name: PHILIPS FTV
[    32.138] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    32.138] (II) RADEON(0): EDID (in hex):
[    32.138] (II) RADEON(0): 	00ffffffffffff00410c000001010101
[    32.138] (II) RADEON(0): 	00150103684024782aabd5a5554d9d25
[    32.138] (II) RADEON(0): 	11505421080081800101010101010101
[    32.138] (II) RADEON(0): 	0101010101011a3680a070381f403020
[    32.138] (II) RADEON(0): 	250080682100001c1b2150a051001e30
[    32.138] (II) RADEON(0): 	48883500806821000018000000fc0050
[    32.138] (II) RADEON(0): 	48494c495053204654560a20000000fd
[    32.138] (II) RADEON(0): 	00384c1e5311000a202020202020009a
[    32.138] (II) RADEON(0): Printing probed modes for output VGA-0
[    32.138] (II) RADEON(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1082 1087 1111 -hsync +vsync (66.6 kHz eP)
[    32.138] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    32.138] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 776 798 -hsync -vsync (47.7 kHz e)
[    32.138] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    32.138] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    32.138] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    32.152] (II) RADEON(0): EDID for output DVI-0
[    32.152] (II) RADEON(0): Output VGA-0 connected
[    32.152] (II) RADEON(0): Output DVI-0 disconnected
[    32.152] (II) RADEON(0): Using exact sizes for initial modes
[    32.152] (II) RADEON(0): Output VGA-0 using initial mode 1920x1080
[    32.152] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    32.152] (II) RADEON(0): mem size init: gart size :3fdee000 vram size: s:20000000 visible:1f7d7000
[    32.152] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    32.152] (==) RADEON(0): DPI set to (96, 96)
[    32.152] (II) Loading sub module "fb"
[    32.152] (II) LoadModule: "fb"
[    32.152] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.246] (II) Module fb: vendor="X.Org Foundation"
[    32.246] 	compiled for 1.15.1, module version = 1.0.0
[    32.246] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    32.246] (II) Loading sub module "ramdac"
[    32.246] (II) LoadModule: "ramdac"
[    32.246] (II) Module "ramdac" already built-in
[    32.246] (II) UnloadModule: "modesetting"
[    32.246] (II) Unloading modesetting
[    32.246] (II) UnloadModule: "fbdev"
[    32.246] (II) Unloading fbdev
[    32.246] (II) UnloadSubModule: "fbdevhw"
[    32.246] (II) Unloading fbdevhw
[    32.246] (II) UnloadModule: "vesa"
[    32.246] (II) Unloading vesa
[    32.246] (--) Depth 24 pixmap format is 32 bpp
[    32.246] (II) RADEON(0): [DRI2] Setup complete
[    32.246] (II) RADEON(0): [DRI2]   DRI driver: r600
[    32.246] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    32.247] (II) RADEON(0): Front buffer size: 8160K
[    32.247] (II) RADEON(0): VRAM usage limit set to 456966K
[    32.268] (==) RADEON(0): Backing store enabled
[    32.268] (II) RADEON(0): Direct rendering enabled
[    32.268] (II) EXA(0): Driver allocated offscreen pixmaps
[    32.268] (II) EXA(0): Driver registered support for the following operations:
[    32.268] (II)         Solid
[    32.268] (II)         Copy
[    32.268] (II)         Composite (RENDER acceleration)
[    32.268] (II)         UploadToScreen
[    32.268] (II)         DownloadFromScreen
[    32.268] (II) RADEON(0): Acceleration enabled
[    32.268] (==) RADEON(0): DPMS enabled
[    32.268] (==) RADEON(0): Silken mouse enabled
[    32.268] (II) RADEON(0): Set up textured video
[    32.268] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    32.268] (II) RADEON(0): [XvMC] Extension initialized.
[    32.268] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    32.269] (--) RandR disabled
[    32.277] (II) SELinux: Disabled on system
[    32.825] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    32.825] (II) AIGLX: enabled GLX_ARB_create_context
[    32.825] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    32.825] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    32.825] (II) AIGLX: enabled GLX_INTEL_swap_event
[    32.825] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.825] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    32.825] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    32.825] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    32.825] (II) AIGLX: Loaded and initialized r600
[    32.825] (II) GLX: Initialized DRI2 GL provider for screen 0
[    32.836] (II) RADEON(0): Setting screen physical size to 507 x 285
[    32.948] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.962] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.962] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.962] (II) LoadModule: "evdev"
[    32.963] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.007] (II) Module evdev: vendor="X.Org Foundation"
[    33.007] 	compiled for 1.15.0, module version = 2.8.2
[    33.007] 	Module class: X.Org XInput Driver
[    33.007] 	ABI class: X.Org XInput driver, version 20.0
[    33.007] (II) Using input driver 'evdev' for 'Power Button'
[    33.007] (**) Power Button: always reports core events
[    33.007] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.007] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.007] (--) evdev: Power Button: Found keys
[    33.007] (II) evdev: Power Button: Configuring as keyboard
[    33.007] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.007] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.007] (**) Option "xkb_rules" "evdev"
[    33.007] (**) Option "xkb_model" "pc105"
[    33.007] (**) Option "xkb_layout" "de"
[    33.011] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    33.012] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.012] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.012] (II) Using input driver 'evdev' for 'Power Button'
[    33.012] (**) Power Button: always reports core events
[    33.012] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.012] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.012] (--) evdev: Power Button: Found keys
[    33.012] (II) evdev: Power Button: Configuring as keyboard
[    33.012] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.012] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    33.012] (**) Option "xkb_rules" "evdev"
[    33.012] (**) Option "xkb_model" "pc105"
[    33.012] (**) Option "xkb_layout" "de"
[    33.013] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0
[    33.013] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    33.013] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    33.013] (II) No input driver specified, ignoring this device.
[    33.013] (II) This device may have been added with another device file.
[    33.013] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    33.013] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    33.013] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    33.013] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    33.013] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    33.013] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc050
[    33.014] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    33.014] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    33.014] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    33.014] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    33.014] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    33.014] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    33.014] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    33.014] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.014] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/0003:046D:C050.0003/input/input7/event4"
[    33.014] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[    33.014] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    33.014] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    33.014] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    33.014] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    33.014] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    33.014] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    33.014] (II) No input driver specified, ignoring this device.
[    33.014] (II) This device may have been added with another device file.
[    33.015] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event2)
[    33.015] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    33.015] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    33.015] (**) Microsoft Wired Keyboard 600: always reports core events
[    33.015] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event2"
[    33.015] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x7f8
[    33.015] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    33.015] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    33.015] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/0003:045E:07F8.0001/input/input5/event2"
[    33.015] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 9)
[    33.015] (**) Option "xkb_rules" "evdev"
[    33.015] (**) Option "xkb_model" "pc105"
[    33.015] (**) Option "xkb_layout" "de"
[    33.016] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event3)
[    33.016] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    33.016] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    33.016] (**) Microsoft Wired Keyboard 600: always reports core events
[    33.016] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event3"
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x7f8
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Found 1 mouse buttons
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Found scroll wheel(s)
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Found relative axes
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: Forcing relative x/y axes to exist.
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Found absolute axes
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: Forcing absolute x/y axes to exist.
[    33.016] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: Configuring as mouse
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: Adding scrollwheel support
[    33.016] (**) evdev: Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[    33.016] (**) evdev: Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.016] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/0003:045E:07F8.0002/input/input6/event3"
[    33.016] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 10)
[    33.016] (**) Option "xkb_rules" "evdev"
[    33.016] (**) Option "xkb_model" "pc105"
[    33.016] (**) Option "xkb_layout" "de"
[    33.016] (II) evdev: Microsoft Wired Keyboard 600: initialized for relative axes.
[    33.016] (WW) evdev: Microsoft Wired Keyboard 600: ignoring absolute axes.
[    33.016] (**) Microsoft Wired Keyboard 600: (accel) keeping acceleration scheme 1
[    33.017] (**) Microsoft Wired Keyboard 600: (accel) acceleration profile 0
[    33.017] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[    33.017] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
```

Sorry for the Microsoft keyboard :p

2. Content of the file /home/jrad/.xsession-errors (opend with "less"):

> Script for none started at run_im.
/home/jrad/.xsession-errors (END)


---

### Post by nfidia on 2015-07-18
Hey Bashing-om,

> **Bashing-om said:**
> 
Does not seem at this time to be of great import, so we proceed and 
I await the results of the reboot/updates.

The updates were unsuccessful, as documented.

Another reboot will do not have an effect on the issue, I strongly guess, but I will do another reboot now and will be back soon here.

---

### Post by nfidia on 2015-07-18
Hi Bashing-om,

Reboot applied. Problem still exits.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-18
nfidia; Hey !

We have made good progress .
The system is stable
The system is upgraded
There are no longer reported dependency issues
The open source driver is loaded

Give me some time now to read the log that you provided, and I will get back soonest.

I do think we are looking good, for the condition we are in .

[INDENT][INDENT]light at the end of the tunnel
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-18
> **Bashing-om said:**
> nfidia; Hey !

We have made good progress .
The system is stable
The system is upgraded
There are no longer reported dependency issues
The open source driver is loaded

Thank you very much, Bashing-om.

> Give me some time now to read the log that you provided, and I will get back soonest.

Yes, of course, don't be hectic. I once had a burnout at work, so please do not hurry. Take your time.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-18
nfidia; Well, well, and well .

Up to this time I have yet to see a problem.
The card is identified, the driver is identified and the driver is loaded.
EDID is available and the display resolution is identified:
> 
 32.152] (II) RADEON(0): Output VGA-0 connected

32.152] (II) RADEON(0): Output VGA-0 using initial mode 1920x1080


So I must inquire;
VGA output: is the TV HDMI, and trying to drive it with VGA, is this resolution above what VGA can provide ? Do you have access to a HDMI cable ? ( "  32.152] (II) RADEON(0): [color=green]Output DVI-0[/color] disconnected " )

BK

The log file appears to be in-complete, is there not more after the time stamp entry "  33.017] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4 " ? As I do expect the final entries in the log to be what the driver 'radeon' is doing.

And NOW we are ready to look at our options. 
[INDENT][INDENT]finally
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-19
Hey, Bashing-om,

> **Bashing-om said:**
> 
So I must inquire;
VGA output: is the TV HDMI, 

The TV screen has both a VGA and a HDMI input. I only use the VGA input.

> and trying to drive it with VGA, is this resolution above what VGA can provide ?

The manual of my TV screen specifies in section "Product information about the "Supported display resolution" among other things a resolution of "1920 x 1080 - 60 Hz (for Full HD only)". This is the resolution you quoted in your last post. But what is that "for Full HD only"?

I could try a lower resolution. Here is the content of the /etc/X11/xorg.conf file of my Debian installation (same machine, same monitor, via VGA):

> Section "Monitor"
        Identifier   "VGA-0"
        Option "Enable" "true"
        Option "PreferredMode" "1360x768"
EndSection

According to the manual of my TV screen, the resolution of 1360 x 768 pixels is _not_ "for Full HD only" (quote from the manual).

Should I create a /etc/X11/xorg.conf file in my Ubuntu installation with the same content as the xorg.conf file of my Debian installation? I do not have that display problem when I run Debian.

> Do you have access to a HDMI cable ? ( "  32.152] (II) RADEON(0): [color=green]Output DVI-0[/color] disconnected " )

No, I am sorry, I do not have a HDMI cable.

> The log file appears to be in-complete, is there not more after the time stamp entry "  33.017] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4 " ? As I do expect the final entries in the log to be what the driver 'radeon' is doing.

I will attach the Xorg.0.log file to this post. To make sure that gedit (which I used to open this file to copy its content here) does not cut its content after a certain amount of characters in a text file.

Oops, having renamed this file to Xorg.0.log.txt I tried to upload this file here. Doesn't work. This web site, i.e. the "Manage Attachments" window, says:

> The following errors occurred: Xorg.0.log.txt: Your file of 39.8 KB exceeds the forum's limit of 19.5 KB for this filetype.

I will now manually look at the end of the Xorg.0.log file using the "less" command to find out if the lines about my Microsoft keyboard are really the last lines of this file.

Result: This is a quote from this file which I opened with "less":

> [    33.277] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
(END)

So this file really ends with the lines about my keyboard.

---

### Post by Bashing-om on 2015-07-19
nfidia; Well ......

The thing is VGA is not HD, The bandwidth in VGA will not support higher resolutions ( can not cram 7 pounds of sugar in a 5 pound sack ) . I do have my learning cap on. I can accept that the radeon driver in a VGA configuration just can not perform. BUT, let's give this a whirl as we know that the resolution "should" be " 1360x768 " :
Our 1st, easiest, option is to try and reset the resolution from within the GUI "display" settings.
What results when you attempt to change the resolution to "  1360x768 " ?

And in respect to setting up an /etc/X11/xorg.conf for the radeon driver, sure we can try and see what happens. With DKMS (Dynamic Kernel Mode Setting) that file is no longer generally required, but I believe if it or :
- The new X.org prefers to autodetect everything (DKMS at work ). WE need to be careful with the xorg.conf entries. The general advise is put our override/tweaks into /etc/X11/xorg.conf.d as "xxxx.conf" named files. -

these files exist, they will be used.

-----------------
The less /var/log/Xorg.0.log file: Yuk, Not sure what to make of it ! I also run an old ATI card and use the radeon driver But I do have a DVI monitor and a HDMI cable. Up to the end of the respective files our results are the same ( not counting that I run 1600X900 ) .. The finals in my file :
```

[    27.152] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.152] (II) RADEON(0): Modeline "1600x900"x0.0  118.25  1600 1688 1856 211
2  900 903 908 934 -hsync +vsync (56.0 kHz eP)
[    27.152] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  6
00 601 605 628 +hsync +vsync (37.9 kHz e)
[    27.152] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  6
00 601 603 625 +hsync +vsync (35.2 kHz e)
[    27.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  48
0 481 484 500 -hsync -vsync (37.5 kHz e)
[    27.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  48
0 489 492 520 -hsync -vsync (37.9 kHz e)
[    27.152] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  48
0 483 486 525 -hsync -vsync (35.0 kHz e)
[    27.152] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  48
0 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.152] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  40
0 412 414 449 -hsync +vsync (31.5 kHz e)
[    27.152] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 131
2  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    27.152] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 132
8  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    27.152] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 134
4  768 771 777 806 -hsync -vsync (48.4 kHz e)
<snip, several pages >
00 601 604 625 +hsync +vsync (46.9 kHz e)
[    30.496] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    30.496] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    30.496] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    30.496] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
(END)

```
so I am unsure what to make of the fact that your system does not " DDC gathered Modelines: " <- The reason for my confusion !

We poke at this and see 
[INDENT][INDENT]see what we can do .
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-19
Hi Bashing-om,

HD means "High Definition", right?

> **Bashing-om said:**
> BUT, let's give this a whirl as we know that the resolution "should" be " 1360x768 " :
Our 1st, easiest, option is to try and reset the resolution from within the GUI "display" settings.
What results when you attempt to change the resolution to "  1360x768 " ?

In Gnome, via a right-click on the Desktop I opened the Settings Manager => Hardware => Display:

These are the resolutions which are offered there (none was selected when I opened the Display window):

- 1024x768
- 800x600
- 848-480
- 640x480

The resolution 1360x768 and this other one (1920x1080 pixels) are not listed there.

I gave it a try and selected 1024x768 pixels, having booted a generic kernel.

Result: the resolution had been changed, but the problem still exists.

I am currently running the low latency kernel, and I did not touch the settings in the Display window of the Settings Manager. The resolution I see here is higher than 1024x768 pixels, but I do not know which resolution has been set to the display, at least according to what I could find out via the Display manager of the Settings Manager (same setting possibilities as described above).

> And in respect to setting up an /etc/X11/xorg.conf for the radeon driver, sure we can try and see what happens. With DKMS (Dynamic Kernel Mode Setting) that file is no longer generally required, but I believe if it or :
- The new X.org prefers to autodetect everything (DKMS at work ). WE need to be careful with the xorg.conf entries. The general advise is put our override/tweaks into /etc/X11/xorg.conf.d as "xxxx.conf" named files. -

OK. So you currently do not recommend to set up such a file, so I will not do that.

> so I am unsure what to make of the fact that your system does not " DDC gathered Modelines: " <- The reason for my confusion !

Yes. Hm. Any idea what to do next? 

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-19
nfidia; Yeah !

I do have a couple of thoughts. As we can not achieve the effect desired from "display settings" . Let's take a look at setting the resolution explicitly from grub.
Preliminary, we want to insure that we do not overdrive any components. So, let's look at what grub will support:
Reboot to grub's boot menu, and press the 'c' key for (c)ommand line.

Is 1360x728 listed as a supported mode when grub command 
```

vbeinfo

```
is executed ?
If so we can make an edit !

[INDENT]and we see what other options that we can come up with
[/INDENT]

---

### Post by nfidia on 2015-07-19
Hi Bashing-om,

Well, when I execute "c" at the boot prompt at the line of the Ubuntu low latency driver and then enter "vbeinfo" behind the grub prompt, then I see a list of resolutions. But this list is too long, so I only see the lower part of that list, the upper part is hidden, and I cannot scroll up/down that list to view all resolution entries of that list. 

I need something like a " | more" command extension, as one can enter in a Linux terminal, so that I can scroll down that list.

Is there such a command which I can combine with the "vbeinfo" command for the grub shell?

Best regards,

nfidia.

PS: I have read on the Internet that I can enter "help" behind the grub prompt Will do that now, maybe I find an answer to my question.

PPS: If there is no answer to my question, should I maybe install xandr? This programme should display all possible resolutions, but I do not know if such a list, generated by xandr, is the same list as generated by the vbeinfo command behind the grub prompt.

---

### Post by nfidia on 2015-07-19
Hi Bashing-om,

> **nfidia said:**
> PS: I have read on the Internet that I can enter "help" behind the grub prompt Will do that now, maybe I find an answer to my question.

The "help" command works, but again the same problem: the list of all commands that are possible behind the grub prompt is too long, so that I cannot view all possible commands, because only the lower part of this list is displayed, and I cannot scroll up that list.

So is there something like the " | more" command extension for the grub shell?

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-19
nfidial Youch,

Again, I had not thought of the possibility of the info scrolling off the screen.
Yeah, there is a means to cope !
At the grub > prompt enter:
```

set pager=1

```
and the page up/page down keys will work to "page" through the output.

-------------------------
I have been doing a bit of looking about in respect to VGA/DVI conversions: Not a direct help for our issue, but worth the info:
[http://ubuntuforums.org/showthread.php?t=2284167](http://ubuntuforums.org/showthread.php?t=2284167)

grahammechanical is a source I highly trust.
-----------------

And in respect to ' xandr '; Yes, in my mind also .. In due time we may arrive at it . I would prefer a grub approach first . Keep this as simple as possible.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]many paths to one end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-19
Hi Bashing-om,

Thanks for the "set pager=1" information. Now I could see/scroll down the whole list of possible resolutions at the grub prompt. But I am sorry to tell you that 1360x728 is not listed there.

> **Bashing-om said:**
> 
I have been doing a bit of looking about in respect to VGA/DVI conversions: Not a direct help for our issue, but worth the info:
[http://ubuntuforums.org/showthread.php?t=2284167](http://ubuntuforums.org/showthread.php?t=2284167)

grahammechanical is a source I highly trust.

Thanks for that information. I just read grahammechanical's first post in that thread, but not more. He/she recommends to switch from a VGA to a HDMI cable. If I would do that, then I fear that I get problems with the display of my Debian installation (2nd Linux installation on my machine), so I prefer to keep my VGA cable connection between my machine and my TV screen.

I hope this is okay for you. 

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-19
nfidia; Yeah !

We are going to work with what we have to work with.

My 1st priority is to get you a usable terminal display.
Here is the way I do it :
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[color=red]GRUB_GFXMODE=1600x900[/color]

```
By editing the "GRUB_GFXMODE=" line in the /etc/default/grub file. But we must have a known supported resolution before we tell the kernel what to do. Again, the kernel will do as told and in that process burn up a component if not correct !

So, how about we pick a supported mode as indicated from the 'vbeinfo' output and edit the file ( make a backup first ) and see what results upon a reboot and booting to terminal ? - If you make an edit ' GRUB_CMDLINE_LINUX_DEFAULT="text" ' to this config file you will boot to terminal rather than to a GUI login .

Once we have a seeable display we can run the 'xrandr' for the final tweaks .

[INDENT][INDENT]Now, that is what I think
[INDENT][INDENT][INDENT]your thoughts ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-19
nfidia; scatter brained, me.

I again did not think it through. Any time one edits a grub config file ( /etc/default/grub), one has to:
```

sudo update-grub

```
to propagate the change to the system.

[INDENT][INDENT]awaiting to see results
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-20
Hi Bashing-om,

I am currently running my Debian installation, to have a GUI.

Yes, I remembered that one needs to run a certain command having changed something in the grub configuration ;)
So having changed the content of that file I ran "sudo update-grub".

This is the current content of the file /etc/default/grub in my Ubuntu installation:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x960

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Result: Having selected f. e. the Ubuntu low latency kernel in the grub menu, Ubuntu starts in text mode. First everything looks fine, i. e. all information about the boot process is completely displayed by the TV screen. But then the display changes again to what is here the issue I am confronted with: the left edge of the display is cut, i.e the left edge of the display area is not visible, and at the end of the boot process the prompt is only partly visible.

Do you still think this issue has something to do with X? My Ubuntu installation has (again) not been started in graphical mode, and the problem still exists.

I will now remove the modified /etc/default/grub file in my Ubuntu installation and put pack in place my backup of that file. I have access to that file in my Ubuntu installation from within Debian (no need to mount the appropriate partition). Then I will again execute the command "sudo update-grub" in Ubuntu, which I need to partly type in blindly.

Best regards,

nfidia

---

### Post by nfidia on 2015-07-20
Hi Bashing-om,

> **nfidia said:**
> I will now remove the modified /etc/default/grub file in my Ubuntu installation and put pack in place my backup of that file. I have access to that file in my Ubuntu installation from within Debian (no need to mount the appropriate partition). 

Done.

> Then I will again execute the command "sudo update-grub" in Ubuntu, which I need to partly type in blindly.

I have a problem: When I start Ubuntu, it now (still) starts in text mode. As described before, after a while the boot messages are cut at the left. So at the end I see a prompt that is cut at the left. When I then enter the command "sudo update-grub" (I can only see the characters "o update-grub", having typed them in), appy the ENTER key, and then enter my password, apply the ENTER key again, then nothing happens, even if I wait a certain while. No output in the console. Normally this command lists all operating system installations on a machine, but this is not the case. So I cannot not update the grub configuration in Ubuntu, so I do not have a GUI again in Ubuntu.

I repeated two times the steps described above. Everytime the console tty1 behaved as described above.

I checked the Ubuntu 14.04.2 installation DVD whether it provides a rescue or recovery mode when you start it as a boot medium. No, it doesn't.

Now I am stuck.

---

### Post by Bashing-om on 2015-07-20
nfidia; Yuk -> Trails troubles and Tribulations.

I guess now we put cvt -> xrandr on hold while we investigate a booting issue. I am once more mystified as to what the kernel is doing that effects changing the resolution. I got a thought to pass to the kernel a resolution setting from grub's boot parameters.

To address booting of course has become the higher priority.
I have broke grub many times, and have gained a modest amount of experience regaining boot.
My starting point is to see if I can boot the system from grub. The thing here is that one has to know the arrangement of the system partitions and file structure. We can find that out. Either from an external source or from grub directly .

Grub way:
Boot to the grub menu -> 'c' key for a command line interface.
- we need to know what partition ubuntu is installed to, and on what partition '/' exist on -
What results from terminal commands:
```

ls -al

```
That gives a list of all the hard drives the system is aware of, Let's say now that ubuntu is installed onto the 1st hard drive, and indications are that it is installed to the 1st hard drive 1st partition; then we can look at it and see if that is the target file system:
```

ls -al (hd0,msdos1)

```
Check and make sure this is the file system we want:
```

ls -al (hd0,msdos1)/etc/default/grub

```
As you gather the syntax is :
hd0 == 1st hard drive
a second hard drive would be  hd1
Partition syntax is -> msdos1 is the 1st partition; msdos2 being the second and so forth .
Such that if one had a file system on the 3rd hard drive 4th partition, then -> " (hd2,msdos4) "
the hd numbering begins at 0. the partitioning numbering begins at 1.

So we try and boot, in my below procedure the hard drive is the 1st and ubuntu is on the 1st partition:
from the grub prompt we execute terminal commands:
```

linux (hd0,msdos1)/vmlinuz root =/dev/sda1 ro
initrd (hd0,msdos1)initrd.img
boot

```
Where we tell grub where it's files are to boot from, and grub tells the kernel where it's files are; 'boot' to execute .

Depending on what happens is what we adjust - if it does not boot ! Grub is very good about giving us all kinds of help to help it to boot. Grub is also a very complex system, and I do get lost after a certain point - in what is transpiring in what is called " kernel space " ; and being intimate with the various control files, I am not .

But I bet we can finger this non-booting issue out too.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-20
Hi Bashing-om,

Thanks again for your reply.

I have problems with your grub commands.

I have one single hard disk.

The root partition of Ubuntu is installed in /dev/sda1

I did not create an indivual partition for /etc in my Ubuntu installation.

So the file /etc/default/grub of my Ubunt installation should be located in (hd0,msdos1)

When I run the command behind the grub prompt

```
ls (hd0,msdos1)
```

I get the same result when I run the command

```
ls -al (hd0,msdos1)
```

=> no files in (hd0,msdos1) are listed. I cannot see any file names. Only information about when the partition was modified last, and the block size or its starting point, I cannot really remember

When I execute the command

```
ls -al (hd0,msdos1)/etc/default/grub
```

, then grub tells me that this file cannot be found, although I can see that file of my Ubuntu installation within my Debian installation, having mounted /dev/sda1

So the command

```
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
```

also results in "file not found" or something similar, although I can see the vmlinuz file of my Ubuntu installation within my Debian installation, having mounted /dev/sda1

Debians primary partition is, by the way, installed in /dev/sda2

Best regards,

nfidia

---

### Post by nfidia on 2015-07-20
Update:

I brought my Ubuntu system back to the situation from before this morning, i.e. Ubuntu starts now again into GNOME.

I did that by using the "e" key in the grub menu, then editing a line which contained the word "text", which I replaced with the words "quiet splash". Then I started Ubuntu, then I got my GUI again, then I opened a console within the GUI, then I ran "sudo update-grub".

Regarding the grub commands behind the grub command I in between found out that the first line of starting Ubuntu by hand should be:

```
linux (hd0,msdos1)/vmlinuz ro root=/dev/sda13
```

, because /dev/sda13 is the partition of the /boot directory of my Ubuntu installation.

But when running this command, grub still tells me that it cannot find the vmlinuz file.

@Bashing-om, do we still need to try to start Ubuntu by manually giving grub starting commands?

---

### Post by Bashing-om on 2015-07-20
nfidia; Hey;

Good deal that you are now booting, that is the point of working grub to boot,

OK, now that you are booting, lets give the kernel an explicit resolution we want to use:
Once more, edit /etc/default/grub :
the line:
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
Add also the boot parameter:
video=VGA-1:1280x960-24@60
to look like:
```

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=VGA-1:1280x960-24@60"

```
Save the file, and update-grub for the change to propogate.
Reboot the system, 
What now ?

As a guess that the output is '1' (VGA-1).
WE could and should run :
```

xrandr -q

```
to identify the display port, and the suggested resolutions.
----------------
A bit of a change in direction: I am deeply concerned that you are presently booting the utopic kernel, 
> 
Linux music 3.16.0-43-lowlatency #58~14.04.1-Ubuntu SMP PREEMPT Mon Jun 22 10:48:48 UTC 2015 i686 athlon 

as this Thursday that release, and as well that kernel, goes End_Of_Life , To this time we have not been able to get that kernel updated to 'vivid's' . At some point soon we are going to have to address that issue.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-20
Hi Bashing-om,

I just applied your proposal about the arguments for the "GRUB_CMDLINE" parameter. But I changed them a little bit, with regard to the color depth, because I looked at the results of the "vbeinfo" command at the grub prompt. So this line in the /etc/default/grub file now looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=VGA-1:1280x960-32@60"

```

vbeinfo does not list "24" as a possible color depth for 1280x960.

So now I rebooted Ubuntu with this change in the grub configuration.

But the resolution in GNOME did not change. It is not 1280x960 pixels, but a higher resolution, the same resolution as before my changes to the /etc/default/grub file.

xrandr -q gives:

```
> jrad@music:~/Schreibtisch$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x54)  138.5MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1082 end 1087 total 1111           clock   59.9Hz
jrad@music:~/Schreibtisch$ 
```

=> 1280x960 pixels is not listed here, so do I need to run Ubuntu with a maximum of 1024x768 pixels?
=> 1920x1080 pixels is quite small for my eyes.
=> Hm.

[quote]A bit of a change in direction: I am deeply concerned that you are presently booting the utopic kernel, 

as this Thursday that release, and as well that kernel, goes End_Of_Life , To this time we have not been able to get that kernel updated to 'vivid's' . At some point soon we are going to have to address that issue.

Hm, I do not really know what you mean, but I guess when a newer kernel will be released, we need to fix this issue again?

By the way: the problem still exits.

---

### Post by nfidia on 2015-07-20
Update:

I just saw in the output of the xrandr command, that the display definition of my tv screen is_ VGA-0_. 

In that GRUB_CMDLINE_LINUX_DEFAULT parameter I had specified _VGA-1_ as the display definition of my tv screen:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=_VGA-1_:1280x960-32@60"
```

This explains why my monitor did not switch its resolution to 1280x960 pixels, but kept to 1920x1080 pixels. 

Because of this, should I change the parameters of the GRUB_CMDLINE_LINUX_DEFAULT parameter, so that it refers to _VGA-0_, and to a resolution of _1280x960_ pixels, so that this line would look like this?

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=VGA-0:1280x960-32@60"
```

Or would this destroy my tv screen and/or my graphics card?

---

### Post by Bashing-om on 2015-07-20
nfidia; Yepper !

you got it :
> 
As a guess that the output is '1' (VGA-1).

VGA-0 connected 1920x1080+0+0

So yeah, readjust for 'VGA-0' and whatever resolution and color depth that you think is usable.

We get a working display, then I refocus to get the later kernel installed.

I keep saying this ->
[INDENT][INDENT]we do make progress
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-21
Hi Bashing-om,

Now the /etc/defaulr/grub file has a line with this content:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=_VGA-0_:1280x960-32@60"
```

Having applied the change in this line I applied a "sudo update-grub" and restarted Ubuntu.

The result:

The resolution is now different, i.e. "smaller" than before, if one looks at the screen. Desktop icons a.s.o. are now a little bit bigger. Thus, a resolution change has happend.

Problem still exists, by the way.

> **Bashing-om said:**
> 

We get a working display, then I refocus to get the later kernel installed.

I keep saying this ->
[INDENT][INDENT]we do make progress
[/INDENT][/INDENT]

OK ;)

---

### Post by Bashing-om on 2015-07-21
nfidia; Hey, Hey !

We do make progress.

OK, is text as you like it ? Perhaps now change the theme for the desktop icon set ? 
I do not have a gnome desktop that I can test with so can not advise on the where with to change the theme; but I would and do expect that within the GUI display settings one can effect that .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-21
Hi Bashing-om,

> **Bashing-om said:**
> We do make progress.

That's good.

> OK, is text as you like it ? Perhaps now change the theme for the desktop icon set ? 
I do not have a gnome desktop that I can test with so can not advise on the where with to change the theme; but I would and do expect that within the GUI display settings one can effect that .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

No, I do not need to change GNOME because I will replace it by XFCE, as soon as this problem here is solved.

Cause I wanna save RAM for music production.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-21
nfidia; K;

The system is stable, just a resolution issue, If it is your desire to have xfce as the Desktop Environment -
I like xfce myself, is my preference - May as well install now and see what the resolution is like in xfce, no ?

It is your system and time
[INDENT][INDENT][INDENT]I am just here to help
[/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-21
Hi Bashing-om,

Let me first say that I want to thank you for all your support and efforts so far. I am happy that you help me ;)

> **Bashing-om said:**
> nfidia; K;

The system is stable, just a resolution issue, If it is your desire to have xfce as the Desktop Environment -
I like xfce myself, is my preference - May as well install now and see what the resolution is like in xfce, no ?

I think it is not a good idea to install XFCE right now. 

I fear that if I install XFCE right now, then I will be confronted with the same problem: I cannot see the start button in the upper left corner, thus I cannot open a terminal via the start button. And very possibly I will not completely see the prompt line of a TTY when I install XFCE right now. And I very probably would not be able to open a terminal by right-clicking the XCFE desktop, as it is the case in GNOME.

(By the way, I cannot see the bottom task bar of GNOME, only the upper one. Isn't there a bottom taskbar in GNOME by default?)

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-21
nfidial OK;

Back then to a resolution issue in gnome; Where we are now with adding a boot parameter to the kernel is the least intrusive, easiest to maintain option to effect the resolution.

So, is the text rending acceptable ? What results with changing the resolution parameters from that of ":
> 
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet video=VGA-0:1280x960-32@60"
Having applied the change in this line I applied a "sudo update-grub" and restarted Ubuntu.

The result:

The resolution is now different, i.e. "smaller" than before, if one looks at the screen. Desktop icons a.s.o. are now a little bit bigger. Thus, a resolution change has happend.

Problem still exists, by the way.


Lastly changing the icon theme set has what effect ?

[INDENT][INDENT]just a didling matter now I trust .
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-21
Hey Bashing-om,

> **Bashing-om said:**
> So, is the text rending acceptable ? What results with changing the resolution parameters from that of ":

Everything fine, but the problem still exists.

> Lastly changing the icon theme set has what effect ?

Changing the icon theme has (of course) no effect on the problem. The problem still exists.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-21
nfidia; Huh ?

> 
Everything fine, but the problem still exists.
bk
Changing the icon theme has (of course) no effect on the problem. The problem still exists.


I am under the impression that the screen display is at a position that the left side is not accessible. Resetting the display resolution had no effect on seeng the left side ?
Is there 'display' options on the TV for positioning ?

[INDENT][INDENT]as I flounder on along
[/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-21
Hi Bashing-om,

> **Bashing-om said:**
> I am under the impression that the screen display is at a position that the left side is not accessible.

Yes, this is correct.

> Resetting the display resolution had no effect on seeng the left side ?

Yes, this is correct.

> Is there 'display' options on the TV for positioning ?

You mean buttons provided by the TV screen which you can use to position the display area? No, they do not exist.

And, let me add this again, this problem does not seem to be GNOME-related, because the problem also occurs when I start Ubuntu in text mode (TTY1 is also cut at the left edge of the screen). I do not know if this problem is caused by the open source radeon driver, or by a display driver which is loaded _before_ the open source radeon driver is loaded during the boot process.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-21
nfidia; Yeah ;
same same thought:
> 
 I do not know if this problem is caused by the open source radeon driver, or by a display driver which is loaded before the open source radeon driver is loaded during the boot process.


As bios has a graphics driver ->
grub has it's graphics driver ->
the Kernel has it's graphics driver ->
And then finally the GUI loads it's graphics driver .

As when booting up in text mode, initially the display is good, lends to my mind the credence that the kernel driver is nuts .
Now I putting on think'n cap ... 

[INDENT][INDENT]I will be back .
[/INDENT][/INDENT]

---

### Post by blm-ubunet on 2015-07-21
Isn't this problem just overscan problems?
TVs normally have excessive overscan on the VGA input because it is not really intended to be driven by computer.
Many TVs only support specific default standardized video modes over VGA.
My old Philips TV does not provide any EDID/DDC over VGA.
The issue you see could be that the video drivers have different default underscan on VGA & the TV has different amount of overscan on the VGA input for each different video mode you apply.

As you already know?
The native resolution of your TV is 1366x768
[http://www.lcd-compare.com/televiseur-PHI26PFL3606H-PHILIPS-26PFL3606H.htm](http://www.lcd-compare.com/televiseur-PHI26PFL3606H-PHILIPS-26PFL3606H.htm)

Does you TV have a menu option to set VGA to "PC Mode" or PC input & "no scaling" or "unscale" or pixel mapping ?
Your TV could have a service mode for overscan adjustment. You would need to find the service password.
Some TVs require the input to be given a precise name.

And VGA is more than capable of what is labelled for consumer electronics as HD (low resolution for CAD workstation).

---

### Post by nfidia on 2015-07-22
Hi Bashing-om,

> **Bashing-om said:**
> 
As bios has a graphics driver ->
grub has it's graphics driver ->
the Kernel has it's graphics driver ->
And then finally the GUI loads it's graphics driver .

As when booting up in text mode, initially the display is good,

Yes, that's the case. And then, at a certain point during the boot process of Ubuntu, the display turns into my problem: the left edge of the display area is cut at the left side of my monitor.

> lends to my mind the credence that the kernel driver is nuts .

Yes, that could be the case.

Best regards,

nfidia

---

### Post by nfidia on 2015-07-22
Oh, thank you Bashing-om, I just discovered a mistake that I made in my issue description at

[http://askubuntu.com/questions/643232/ubuntu-14-04-2-display-area-out-of-alignment](http://askubuntu.com/questions/643232/ubuntu-14-04-2-display-area-out-of-alignment)

I do not have a PHILIPS _26_PFL3606H, but a PHILIPS _22_PFL3606H

I corrected this mistake in my issue description at Ask Ubuntu.

The manual of my TV screen specifies in section "Supported display resolutions - computer formats" the resolution of 1920x1080 pixels as the highest resolution (this resolution is for full HD only).

---

### Post by nfidia on 2015-07-22
Hi Bashing-om,

> **blm-ubunet said:**
> Does you TV have a menu option to set VGA to "PC Mode" or PC input & "no scaling" or "unscale" or pixel mapping ?
Your TV could have a service mode for overscan adjustment. You would need to find the service password.
Some TVs require the input to be given a precise name.

I just checked the possibilities my TV screen offers with regard to changing its settings. And I found out that its adjustments menu offers the possibility to change the location of the display area, so, having started Ubuntu I moved the display to the right, so that the display area now fits into the monitor area.

So then I thought "But now my Debian installation will have a display problem, the display area will be moved to the right, and I will have the same problem which I had in Ubuntu, but with the difference that the right edge of the display area will be cut at the right edge of the monitor.

But this is not the case, as I found out when I booted into Debian: everything is fine with regard to the display of Debian's GUI (KDE).

So the issue is solved. Now the display area is correctly displayed in Debian and in Ubuntu.

I feel a little bit stupid now.

Bashing-om, thanks a lot for all your efforts and help. I am so sorry that I did not check the adjustments menu of my TV screen before. This thread now contains 8 pages, so much work for you for an easy-to-solve-problem, I am so sorry for that. I will send you a bath tub full of German beer ;)

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-22
nfidia; Well well !

And all is well .. The only thing of import is that a solution was found. I add this experience to my knowledge base . I will put the dirty hacks to the display manager's config files back in the tool box as not required in this event.

I do hope that the experience has led to you being the more comfortable with this our operating system of choice .

[INDENT][INDENT]we keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-22
@blm-ubunet: I just saw that you pointed me to checking the settings of my TV screen. Possibly you read all the existing posts in this thread before you posted your post here, so a lot of work you did for solving my problem. Thanks for your help, too.

Best regards,

nfidia

---

### Post by nfidia on 2015-07-22
Hi Bashing-om,

Thanks for your words. 

> **Bashing-om said:**
> I add this experience to my knowledge base.

Yes, I already had in mind that you would do this.

> I do hope that the experience has led to you being the more comfortable with this our operating system of choice.

Yes. Now I can continue to set up Ubuntu Studio for music production means. Whenever I find an error or a bug, I will report this here. To improve Ubuntu Studio.

Best regards,

nfidia.

---

### Post by Bashing-om on 2015-07-23
@ nfidia :)

Good deal, well done. Do good things ! We catch ya on the upside .

@ blm-ubunet; Your input is so appreciated !

together, we make it happen .

[INDENT][INDENT]'buntu;
[INDENT][INDENT][INDENT]ain't it wonderful
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-23
Hey folks,

An update: 

1. Problem solved, as reported.

2. Problem occurs again under the following circumstances:

If I delete the "splash" argument in the /etc/default/grub file behind the "GRUB_CMDLINE_LINUX_DEFAULT" switch (in order to get the Ubuntu boot messages displayed during boot), then "sudo update-grub", then a reboot, then:

1. The boot messages are displayed correctly, i.e. completely within the monitor area

2. The GUI is then started, but displayed out of alignment, i.e. the left side of the display area is cut at the left edge of the monitor (I cannot see the start button), and there is a black area between the right edge of the display area and the right montor edge (thus the same behaviour as reported here in my first post). Additionally, the resolution seems to be 1024x768, thus not the resolution which is specified in the /etc/default/grub file behind the "GRUB_CMDLINE_LINUX_DEFAULT", i.e. 1280x960 pixels.

3. When I specify the argument "splash" in the /etc/default/grub file behind the "GRUB_CMDLINE_LINUX_DEFAULT" switch again , then "sudo update-grub", then a reboot, then:

Everything is fine again: GUI with resolution as specified in the  /etc/default/grub file, and display area correctly/completely displayed within the monitor area. But I cannot see the boot messages during boot.

Keen on creating a new thread regarding this issue (by myself)?  :-D Maybe you do not have any ideas anymore for how to solve this new issue.

Best regards,

nfidia

---

### Post by blm-ubunet on 2015-07-23
Your TV display is 1360x768.. it makes no sense to drive it at any other resolution. It is only an HD-ready display with a prescaler. For computer monitor use it should be used in native resolution only (or integer multiples of).

Adjusting the screen offset seems like a band-aid solution because each possible resolution requires a new/different band-aid. You need to try to defeat the overscan on VGA by enabling direct pixel mapping/ no-scaling. Then any supported video mode (TV) will at least (hopefully) be completely visible.

Are you using gnome-shell (gnome3) or gdm or gdm-greeter ?
All of these interfere with screen resolution by executing "xrandr --auto" repeatedly..

You are still using the open source radeon driver ? (check in /var/log/Xorg.0.log).
The open source radeon driver is a kernel mode setting (KMS) driver; it can correctly set the required resolution from grub thru' to greeter to GUI desktop.
Debatable if this is actually possible with gnome3.
You still have to set the exact required resolution in grub config file, the default safe resolution will be something 4:3ish like 1024x768..
If the radeon driver is not loading then you get vesa or framebuffer driver both with terrible video mode options.

---

### Post by nfidia on 2015-07-24
Hi blm-ubunet,

> **blm-ubunet said:**
> Your TV display is 1360x768.

In my very first post regarding this issue (in my thread at Ask Ubuntu) I made a  mistake and specified a slightly different model of my Philips TV screen. During this thread I discovered this error and corrected my very first post at Ask Ubuntu. So this is my TV screen: it's a PHILIPS 22PFL3606H.

The manual of my TV screen specifies 9 different resolutions for computer display. 2 of these resolutions are "for Full HD only", and these resolutions are:

- 1680x1050
- 1920x1080

> it makes no sense to drive it at any other resolution. It is only an HD-ready display with a prescaler.

As said before, my TV screen offers 9 different resolutions, from which only 2 resolutions are "for Full HD only".

So it should be okay if I use a non-"for Full HD only"-resolution. 

> For computer monitor use it should be used in native resolution only (or integer multiples of).

My second installation (Debian 7.8) is displayed with 1360x768. The display of its boot messages is correct, and the display of its GUI (KDE) is correct.

But I just made a test: I specified in the file /etc/default/grub behind the GRUB_CMDLINE_LINUX_DEFAULT switch only the argument "quiet", so I did not specify any resolution behind this switch. Then "sudo update-grub", then a reboot: problem still exists (boot messages are correctly displayed within the monitor area, but when the GUI is started, then the left side of the display area is cut, and there is a black area right to the right edge of the display area, and the displayed resolution seems to be 1024x768.

> Adjusting the screen offset seems like a band-aid solution because each possible resolution requires a new/different band-aid. You need to try to defeat the overscan on VGA by enabling direct pixel mapping/ no-scaling. Then any supported video mode (TV) will at least (hopefully) be completely visible.

What is "overscan"?

How do I enable direct pixel mapping/no-scaling?

> Are you using gnome-shell (gnome3) or gdm or gdm-greeter ?

I am using XFCE. From the very beginning of my Ubuntu Studio installation. I wasn't aware of this because I could not see the whole display area. I could not see the start button in the left upper corner, so I thought I would use GNOME. I am not really familiar with how GNOME looks like because I normally use KDE.

> All of these interfere with screen resolution by executing "xrandr --auto" repeatedly..

OK. But I did not use "xrandr --auto" until now.

> You are still using the open source radeon driver ? (check in /var/log/Xorg.0.log).

This is the result of the command "cat /var/log/Xorg.0.log | grep radeon":

> [    30.381] (II) LoadModule: "radeon"
[    30.381] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.490] (II) Module radeon: vendor="X.Org Foundation"

So I am using the radeon Xorg driver.

> The open source radeon driver is a kernel mode setting (KMS) driver; it can correctly set the required resolution from grub thru' to greeter to GUI desktop.
Debatable if this is actually possible with gnome3.

As described above, I am using XFCE.

> You still have to set the exact required resolution in grub config file, the default safe resolution will be something 4:3ish like 1024x768..

I currently use 1280x960, which I specified in the grub file. This resolution is offered by the "vbeinfo" command in the grub shell. This resolution is a 4:3 resolution, too.

> If the radeon driver is not loading then you get vesa or framebuffer driver both with terrible video mode options.

The radeon Xorg driver is loaded, see above.

Best regards,

nfidia.

---

### Post by Bashing-om on 2015-07-24
nfidia; blm-ubunet;

I remain active on this thread. As Gnome is at play here, is gnome interfering with xfce's display ability ?
What applications are running in gnome ?
```

ps aux| grep gnome

```

Does this file exist ?
```

ls -al /etc/pam.d/lightdm

```


I too run xfce as my Desktop Environment ( version 4.10); I am finding that a lot of the documentation for resolution is out of date, and I proceed with caution.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by blm-ubunet on 2015-07-24
I did spot you had updated the TV model.. The technical specs for 22FPL3606 seem hard to find but the native resolution is still	appears to be 1366x768.
The consumer electronics industry made this resolution very common.
Computer video modes are all integer multiples of 16 therefore 1360x768 (as 768/9*16=1360 & (768 modulo 16) = 0). This is very memory & bandwidth efficient for GPU & video decoding.
I'm not sure all video card have built-in video mode of 1366x768.

All TVs & monitors have prescalers. Only internal panels (laptops) do not.
> The manual of my TV screen specifies 9 different resolutions for computer display. 2 of these resolutions are "for Full HD only", and these resolutions are:

- 1680x1050
- 1920x1080
Must be marketing speak because it makes little technical sense; The display is not HD & 1680x1050 is not HD resolution but it was a common computer 16:10 format.
The display can accept HD 1920x1080 and down scale to native 1366x768 therefore it is an HD-ready TV.

Every TV manufacturer has their own marketing name for direct pixel mapping (one-to-one, just-scan, PC-input, no-scale).
You may have to disable all the TVs video processing. Most TVs are no match for a PC video cards post processing.

I'm fairly sure xfce/xubuntu does not interfere by using xrandr because mythbuntu is based on xfce & there would be howls of protest about this in these forums.
You can chose to use lightdm or gdm greeter/display manager but I believe lightdm is the default & you are using that ?

If you tried gnome(3)-shell it is possible that it changed the greeter & display manager to gdm.
It is easy to reconfigure lightdm or purge gdm in synaptic/apt-get/dpkg.
To list install status:
```
sudo dpkg -l *dm
```

---

### Post by nfidia on 2015-07-25
Hi Bashing-om,

Here is the output of "ps aux| grep gnome":

```
jrad@music:~/Schreibtisch$ ps aux| grep gnome
jrad      1493  0.0  0.5  55172 11020 ?        Sl   07:15   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
jrad      1678  0.0  0.6  33024 12576 ?        Sl   07:15   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
jrad      1704  0.0  0.2  17368  4600 ?        Sl   07:15   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
jrad      2063  0.0  0.0   2424  1700 ?        S    07:18   0:00 gnome-pty-helper
jrad      2077  0.0  0.1   6164  2284 pts/0    S+   07:18   0:00 grep --color=auto gnome
jrad@music:~/Schreibtisch$
```

This is the output of "ls -al /etc/pam.d/lightdm":

```
jrad@music:~/Schreibtisch$ ls -al /etc/pam.d/lightdm
-rw-r--r-- 1 root root 752 Dez 11  2014 /etc/pam.d/lightdm
jrad@music:~/Schreibtisch$ 
```

Since I finished the installation of Ubuntu Studio 14.04.2, XCFE is the default desktop. I was not aware of this, until I could see the whole display area. So then I first saw that typical XFCE start button in the upper left corner of my GUI.

If I do the following:

1. Right-clicking the desktop => Applications => Settings Manager
2. Click the "Help" button within Settings Manager 
3. I get asked if I want to read the help stuff online
4. I answer this question with "yes"
5. The following web address is opened in my browser: [http://docs.xfce.org/xfce/xfce4-settings/4.10/start](http://docs.xfce.org/xfce/xfce4-settings/4.10/start)

So my GUI is XFCE.

When I start Ubuntu Studio, I cannot switch between different desktop managers. XFCE is the only desktop manager that I am and have been using so far.

Best regards,

nfidia

---

### Post by nfidia on 2015-07-25
Hi blm-ubunet,

Thanks for all your information. Hm ...

> **blm-ubunet said:**
> You can chose to use lightdm or gdm greeter/display manager but I believe lightdm is the default & you are using that ?

This is the output of "sudo dpkg -l *dm"

```
jrad@music:~/Schreibtisch$ sudo dpkg -l *dm
[sudo] password for jrad: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  gdm            <none>       <none>       (no description available)
un  kdm            <none>       <none>       (no description available)
ii  lightdm        1.10.5-0ubun i386         Display Manager
un  lxdm           <none>       <none>       (no description available)
un  mdadm          <none>       <none>       (no description available)
jrad@music:~/Schreibtisch$
```

So I am using only lightdm.

Best regards,

nfidia

---

### Post by Bashing-om on 2015-07-25
@ nfidia ; Humm ....

This :
> 
jrad      2063  0.0  0.0   2424  1700 ?        S    07:18   0:00 gnome-pty-helper

says gnome is a factor in this, somehow.

And as well these:
> 
-rw-r--r-- 1 root root 752 Dez 11  2014 /etc/pam.d/lightdm
ii  lightdm        1.10.5-0ubun i386         Display Manager

Say we have to work within 'lightdm' rather then xfwm (xfce4) . I am still in a quandary as to the better way to effect the display.
a) Hardware settings
b) xrandr
c) edit a config file -> make up a file:
   1) xorg.conf
   2) A simple call to use xrandr's output (startup applications)
d) How do we make sure there is no conflict between lightdm and xfwm. both are 'windows managers' ?

I go do research, see if I can determine to make an educated guess .

[INDENT][INDENT]oh, that process of learning
[/INDENT][/INDENT]

---

### Post by blm-ubunet on 2015-07-25
@nfidia
Did you post (somewhere in this thread) your /var/log/Xorg.0.log for the "good" debian setup?
And the output from "xrandr"..
Note that your TV is automatically scaling video input to what ever it prefers. That's a workable solution but we need to know the real video mode from the PC.

The Xorg log will confirm a working video mode & the FOSS driver etc.
We can apply that video mode to ubuntu setup.

---

### Post by Bashing-om on 2015-07-25
@blm-ubunet uuoohhhhh !

+1 . outstanding thought !

[INDENT][INDENT]why did I not think of that 
[INDENT][INDENT][INDENT]3 heads ARE better than 1
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nfidia on 2015-07-25
Hi folks,

> **blm-ubunet said:**
> @nfidia
Did you post (somewhere in this thread) your /var/log/Xorg.0.log for the "good" debian setup?

No, but here it is:

```
[    21.751] 
X.Org X Server 1.12.4
Release Date: 2012-08-27
[    21.751] X Protocol Version 11, Revision 0
[    21.751] Build Operating System: Linux 3.2.0-4-amd64 i686 Debian
[    21.752] Current Operating System: Linux samba 3.2.0-4-686-pae #1 SMP Debian 3.2.68-1+deb7u2 i686
[    21.752] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-4-686-pae root=UUID=be8143f8-833b-49f3-af44-dbadfc255081 ro install quiet
[    21.752] Build Date: 09 February 2015  10:12:47AM
[    21.752] xorg-server 2:1.12.4-6+deb7u6 (Julien Cristau <jcristau@debian.org>) 
[    21.752] Current version of pixman: 0.26.0
[    21.752] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.752] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.752] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 26 04:27:38 2015
[    21.792] (==) Using config file: "/etc/X11/xorg.conf"
[    21.792] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.817] (==) No Layout section.  Using the first Screen section.
[    21.817] (==) No screen section available. Using defaults.
[    21.817] (**) |-->Screen "Default Screen Section" (0)
[    21.817] (**) |   |-->Monitor "<default monitor>"
[    21.817] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.818] (==) Automatically adding devices
[    21.818] (==) Automatically enabling devices
[    21.857] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.857] 	Entry deleted from font path.
[    21.939] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.939] (==) ModulePath set to "/usr/lib/xorg/modules"
[    21.939] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.946] (II) Loader magic: 0xb77995a0
[    21.946] (II) Module ABI versions:
[    21.946] 	X.Org ANSI C Emulation: 0.4
[    21.946] 	X.Org Video Driver: 12.1
[    21.946] 	X.Org XInput driver : 16.0
[    21.946] 	X.Org Server Extension : 6.0
[    21.947] (--) PCI:*(0:1:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    21.947] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.947] (II) LoadModule: "extmod"
[    21.964] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.975] (II) Module extmod: vendor="X.Org Foundation"
[    21.975] 	compiled for 1.12.4, module version = 1.0.0
[    21.975] 	Module class: X.Org Server Extension
[    21.975] 	ABI class: X.Org Server Extension, version 6.0
[    21.975] (II) Loading extension SELinux
[    21.975] (II) Loading extension MIT-SCREEN-SAVER
[    21.975] (II) Loading extension XFree86-VidModeExtension
[    21.975] (II) Loading extension XFree86-DGA
[    21.975] (II) Loading extension DPMS
[    21.975] (II) Loading extension XVideo
[    21.975] (II) Loading extension XVideo-MotionCompensation
[    21.975] (II) Loading extension X-Resource
[    21.975] (II) LoadModule: "dbe"
[    21.976] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.976] (II) Module dbe: vendor="X.Org Foundation"
[    21.976] 	compiled for 1.12.4, module version = 1.0.0
[    21.976] 	Module class: X.Org Server Extension
[    21.976] 	ABI class: X.Org Server Extension, version 6.0
[    21.976] (II) Loading extension DOUBLE-BUFFER
[    21.976] (II) LoadModule: "glx"
[    21.977] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.999] (II) Module glx: vendor="X.Org Foundation"
[    21.999] 	compiled for 1.12.4, module version = 1.0.0
[    22.000] 	ABI class: X.Org Server Extension, version 6.0
[    22.000] (==) AIGLX enabled
[    22.000] (II) Loading extension GLX
[    22.000] (II) LoadModule: "record"
[    22.000] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.001] (II) Module record: vendor="X.Org Foundation"
[    22.001] 	compiled for 1.12.4, module version = 1.13.0
[    22.001] 	Module class: X.Org Server Extension
[    22.001] 	ABI class: X.Org Server Extension, version 6.0
[    22.001] (II) Loading extension RECORD
[    22.001] (II) LoadModule: "dri"
[    22.001] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.031] (II) Module dri: vendor="X.Org Foundation"
[    22.031] 	compiled for 1.12.4, module version = 1.0.0
[    22.031] 	ABI class: X.Org Server Extension, version 6.0
[    22.031] (II) Loading extension XFree86-DRI
[    22.031] (II) LoadModule: "dri2"
[    22.031] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.032] (II) Module dri2: vendor="X.Org Foundation"
[    22.032] 	compiled for 1.12.4, module version = 1.2.0
[    22.032] 	ABI class: X.Org Server Extension, version 6.0
[    22.032] (II) Loading extension DRI2
[    22.032] (==) Matched ati as autoconfigured driver 0
[    22.032] (==) Matched vesa as autoconfigured driver 1
[    22.032] (==) Matched fbdev as autoconfigured driver 2
[    22.032] (==) Assigned the driver to the xf86ConfigLayout
[    22.032] (II) LoadModule: "ati"
[    22.069] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    22.079] (II) Module ati: vendor="X.Org Foundation"
[    22.079] 	compiled for 1.12.4, module version = 6.14.99
[    22.079] 	Module class: X.Org Video Driver
[    22.079] 	ABI class: X.Org Video Driver, version 12.1
[    22.079] (II) LoadModule: "radeon"
[    22.080] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.126] (II) Module radeon: vendor="X.Org Foundation"
[    22.126] 	compiled for 1.12.4, module version = 6.14.99
[    22.126] 	Module class: X.Org Video Driver
[    22.126] 	ABI class: X.Org Video Driver, version 12.1
[    22.126] (II) LoadModule: "vesa"
[    22.127] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.148] (II) Module vesa: vendor="X.Org Foundation"
[    22.148] 	compiled for 1.12.1, module version = 2.3.1
[    22.148] 	Module class: X.Org Video Driver
[    22.148] 	ABI class: X.Org Video Driver, version 12.0
[    22.148] (II) LoadModule: "fbdev"
[    22.149] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.149] (II) Module fbdev: vendor="X.Org Foundation"
[    22.149] 	compiled for 1.12.1, module version = 0.4.2
[    22.149] 	ABI class: X.Org Video Driver, version 12.0
[    22.149] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA
[    22.160] (II) VESA: driver for VESA chipsets: vesa
[    22.160] (II) FBDEV: driver for framebuffer: fbdev
[    22.160] (++) using VT number 7

[    22.168] (II) [KMS] drm report modesetting isn't supported.
[    22.168] (WW) Falling back to old probe method for vesa
[    22.168] (WW) Falling back to old probe method for fbdev
[    22.168] (II) Loading sub module "fbdevhw"
[    22.168] (II) LoadModule: "fbdevhw"
[    22.169] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.189] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.189] 	compiled for 1.12.4, module version = 0.0.2
[    22.189] 	ABI class: X.Org Video Driver, version 12.1
[    22.189] (EE) open /dev/fb0: No such file or directory
[    22.189] (II) RADEON(0): TOTO SAYS 00000000fdee0000
[    22.189] (II) RADEON(0): MMIO registers at 0x00000000fdee0000: size 64KB
[    22.190] (II) RADEON(0): PCI bus 1 card 0 func 0
[    22.190] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.190] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    22.190] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.190] (==) RADEON(0): Default visual is TrueColor
[    22.190] (II) Loading sub module "vgahw"
[    22.190] (II) LoadModule: "vgahw"
[    22.190] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    22.198] (II) Module vgahw: vendor="X.Org Foundation"
[    22.198] 	compiled for 1.12.4, module version = 0.1.0
[    22.198] 	ABI class: X.Org Video Driver, version 12.1
[    22.198] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    22.198] (==) RADEON(0): RGB weight 888
[    22.198] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    22.198] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[    22.198] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    22.199] (II) RADEON(0): PCIE card detected
[    22.199] (II) Loading sub module "int10"
[    22.199] (II) LoadModule: "int10"
[    22.199] (II) Loading /usr/lib/xorg/modules/libint10.so
[    22.205] (II) Module int10: vendor="X.Org Foundation"
[    22.205] 	compiled for 1.12.4, module version = 1.0.0
[    22.205] 	ABI class: X.Org Video Driver, version 12.1
[    22.205] (II) RADEON(0): initializing int10
[    22.210] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    22.212] (II) RADEON(0): ATOM BIOS detected
[    22.213] (II) RADEON(0): ATOM BIOS Rom: 
[    22.213] 	SubsystemVendorID: 0x1462 SubsystemID: 0x1612
[    22.213] 	IOBaseAddress: 0xee00
[    22.213] 	Filename: SV32013a.bin
[    22.213] 	BIOS Bootup Message: 
113-MSITV161MS.150 AC12400-100 RV710 DDR2 64BIT 600E/500M                     
[    22.213] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    22.213] (II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffec
[    22.213] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    22.213] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffec
[    22.213] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    22.213] (II) RADEON(0): Default Engine Clock: 600000
[    22.213] (II) RADEON(0): Default Memory Clock: 500000
[    22.213] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    22.213] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    22.213] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 16000
[    22.213] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 6000
[    22.213] (II) RADEON(0): Maximum Pixel Clock: 400000
[    22.213] (II) RADEON(0): Reference Clock: 27000
[    22.213] drmOpenDevice: node name is /dev/dri/card0
[    22.222] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    22.222] drmOpenDevice: node name is /dev/dri/card0
[    22.226] drmOpenByBusid: drmOpenMinor returns -1
[    22.226] drmOpenDevice: node name is /dev/dri/card1
[    22.230] drmOpenByBusid: drmOpenMinor returns -1
[    22.230] drmOpenDevice: node name is /dev/dri/card2
[    22.234] drmOpenByBusid: drmOpenMinor returns -1
[    22.234] drmOpenDevice: node name is /dev/dri/card3
[    22.239] drmOpenByBusid: drmOpenMinor returns -1
[    22.239] drmOpenDevice: node name is /dev/dri/card4
[    22.243] drmOpenByBusid: drmOpenMinor returns -1
[    22.243] drmOpenDevice: node name is /dev/dri/card5
[    22.247] drmOpenByBusid: drmOpenMinor returns -1
[    22.247] drmOpenDevice: node name is /dev/dri/card6
[    22.251] drmOpenByBusid: drmOpenMinor returns -1
[    22.251] drmOpenDevice: node name is /dev/dri/card7
[    22.255] drmOpenByBusid: drmOpenMinor returns -1
[    22.255] drmOpenDevice: node name is /dev/dri/card8
[    22.260] drmOpenByBusid: drmOpenMinor returns -1
[    22.260] drmOpenDevice: node name is /dev/dri/card9
[    22.264] drmOpenByBusid: drmOpenMinor returns -1
[    22.264] drmOpenDevice: node name is /dev/dri/card10
[    22.268] drmOpenByBusid: drmOpenMinor returns -1
[    22.268] drmOpenDevice: node name is /dev/dri/card11
[    22.272] drmOpenByBusid: drmOpenMinor returns -1
[    22.272] drmOpenDevice: node name is /dev/dri/card12
[    22.276] drmOpenByBusid: drmOpenMinor returns -1
[    22.276] drmOpenDevice: node name is /dev/dri/card13
[    22.280] drmOpenByBusid: drmOpenMinor returns -1
[    22.280] drmOpenDevice: node name is /dev/dri/card14
[    22.285] drmOpenByBusid: drmOpenMinor returns -1
[    22.285] drmOpenDevice: node name is /dev/dri/card15
[    22.289] drmOpenByBusid: drmOpenMinor returns -1
[    22.289] drmOpenDevice: node name is /dev/dri/card0
[    22.297] drmOpenDevice: node name is /dev/dri/card0
[    22.301] drmOpenDevice: node name is /dev/dri/card1
[    22.306] drmOpenDevice: node name is /dev/dri/card2
[    22.310] drmOpenDevice: node name is /dev/dri/card3
[    22.314] drmOpenDevice: node name is /dev/dri/card4
[    22.318] drmOpenDevice: node name is /dev/dri/card5
[    22.322] drmOpenDevice: node name is /dev/dri/card6
[    22.327] drmOpenDevice: node name is /dev/dri/card7
[    22.331] drmOpenDevice: node name is /dev/dri/card8
[    22.335] drmOpenDevice: node name is /dev/dri/card9
[    22.339] drmOpenDevice: node name is /dev/dri/card10
[    22.343] drmOpenDevice: node name is /dev/dri/card11
[    22.348] drmOpenDevice: node name is /dev/dri/card12
[    22.352] drmOpenDevice: node name is /dev/dri/card13
[    22.356] drmOpenDevice: node name is /dev/dri/card14
[    22.360] drmOpenDevice: node name is /dev/dri/card15
[    22.364] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    22.365] (II) RADEON(0): using shadow framebuffer
[    22.365] (II) Loading sub module "shadow"
[    22.365] (II) LoadModule: "shadow"
[    22.365] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    22.366] (II) Module shadow: vendor="X.Org Foundation"
[    22.366] 	compiled for 1.12.4, module version = 1.1.0
[    22.366] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.366] (II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
[    22.366] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    22.366] (II) RADEON(0): Color tiling disabled
[    22.366] (II) Loading sub module "ddc"
[    22.366] (II) LoadModule: "ddc"
[    22.367] (II) Module "ddc" already built-in
[    22.367] (II) Loading sub module "i2c"
[    22.367] (II) LoadModule: "i2c"
[    22.367] (II) Module "i2c" already built-in
[    22.367] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=60000 max=120000; xclk=40000
[    22.367] (II) RADEON(0): Output VGA-0 using monitor section VGA-0
[    22.367] (**) RADEON(0): Option "PreferredMode" "1360x768"
[    22.367] (**) RADEON(0): Option "Enable" "true"
[    22.367] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    22.367] (II) RADEON(0): Output DVI-0 has no monitor section
[    22.367] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    22.367] (II) RADEON(0): Port0:
[    22.367]   XRANDR name: VGA-0
[    22.367]   Connector: VGA
[    22.367]   CRT2: INTERNAL_KLDSCP_DAC2
[    22.367]   DDC reg: 0x7e40
[    22.367] (II) RADEON(0): Port1:
[    22.367]   XRANDR name: DVI-0
[    22.367]   Connector: DVI-I
[    22.367]   CRT1: INTERNAL_KLDSCP_DAC1
[    22.367]   DFP1: INTERNAL_UNIPHY2
[    22.367]   DDC reg: 0x7f10
[    22.367] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    22.626] Dac detection success
[    22.626] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    22.626] finished output detect: 0
[    22.626] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    22.636] Dac detection success
[    22.636] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    22.636] Unhandled monitor type 0
[    22.636] finished output detect: 1
[    22.636] finished all detect
[    22.894] Dac detection success
[    22.894] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    22.894] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[    22.895] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "320x175" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "320x200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "360x200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1024x768i" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "512x384i" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x480" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x512" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "896x672" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "896x672" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "928x696" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "928x696" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "960x720" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "416x312" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    22.895] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "700x525" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "720x450" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "800x512" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[    22.895] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "960x540" (hsync out of range)
[    22.895] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    22.896] (II) RADEON(0): Not using default mode "960x600" (hsync out of range)
[    22.896] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    22.896] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[    22.896] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    22.896] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    22.896] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    22.896] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    22.896] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    22.896] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    22.896] (II) RADEON(0): Printing probed modes for output VGA-0
[    22.896] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz UdP)
[    22.896] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    22.896] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    22.896] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    22.896] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    22.896] (II) RADEON(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    22.896] (II) RADEON(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    22.896] (II) RADEON(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    22.896] (II) RADEON(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    22.896] (II) RADEON(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    22.896] (II) RADEON(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    22.905] Dac detection success
[    22.905] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    22.905] Unhandled monitor type 0
[    22.905] (II) RADEON(0): EDID for output DVI-0
[    22.905] (II) RADEON(0): Output VGA-0 enabled by config file
[    22.905] (II) RADEON(0): Output DVI-0 disconnected
[    22.905] (II) RADEON(0): Using user preference for initial modes
[    22.905] (II) RADEON(0): Output VGA-0 using initial mode 1360x768
[    22.905] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.905] (==) RADEON(0): DPI set to (96, 96)
[    22.905] (II) Loading sub module "fb"
[    22.905] (II) LoadModule: "fb"
[    22.905] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.912] (II) Module fb: vendor="X.Org Foundation"
[    22.912] 	compiled for 1.12.4, module version = 1.0.0
[    22.912] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.912] (II) Loading sub module "ramdac"
[    22.912] (II) LoadModule: "ramdac"
[    22.912] (II) Module "ramdac" already built-in
[    22.912] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    22.912] (II) UnloadModule: "vesa"
[    22.912] (II) Unloading vesa
[    22.912] (II) UnloadModule: "fbdev"
[    22.912] (II) Unloading fbdev
[    22.912] (II) UnloadSubModule: "fbdevhw"
[    22.912] (II) Unloading fbdevhw
[    22.912] (--) Depth 24 pixmap format is 32 bpp
[    22.912] (II) RADEON(0): RADEONScreenInit d0000000 0 0
[    23.048] Output CRT2 disable success
[    23.059] Blank CRTC 0 success
[    23.059] Disable CRTC memreq 0 success
[    23.073] Disable CRTC 0 success
[    23.073] Blank CRTC 1 success
[    23.073] Disable CRTC memreq 1 success
[    23.073] Disable CRTC 1 success
[    23.073] (II) RADEON(0): Dynamic Power Management Disabled
[    23.074] mc fb loc is 00ef00d0
[    23.074] (II) RADEON(0): RADEONInitMemoryMap() : 
[    23.074] (II) RADEON(0):   mem_size         : 0x20000000
[    23.074] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0
[    23.074] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    23.074] (II) RADEON(0): Depth moves disabled by default
[    23.074] (II) RADEON(0): Memory manager initialized to (0,0) (1536,8191)
[    23.074] (II) RADEON(0): Reserved area from (0,1360) to (1536,1362)
[    23.074] (II) RADEON(0): Largest offscreen area available: 1536 x 6829
[    23.075] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    23.075] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x001f0000
[    23.075] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    23.085] (==) RADEON(0): Backing store disabled
[    23.085] (WW) RADEON(0): Direct rendering disabled
[    23.085] (EE) RADEON(0): Acceleration initialization failed
[    23.085] (II) RADEON(0): Acceleration disabled
[    23.085] (==) RADEON(0): DPMS enabled
[    23.085] (==) RADEON(0): Silken mouse enabled
[    23.085] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x007fb000
[    23.085] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00801000
[    23.085] (II) RADEON(0): Largest offscreen area available: 1536 x 6821
[    23.085] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
[    23.090] Output CRT2 disable success
[    23.090] Blank CRTC 0 success
[    23.090] Disable CRTC memreq 0 success
[    23.090] Disable CRTC 0 success
[    23.090] Blank CRTC 1 success
[    23.090] Disable CRTC memreq 1 success
[    23.090] Disable CRTC 1 success
[    23.091] Output CRT2 disable success
[    23.091] Blank CRTC 0 success
[    23.091] Disable CRTC memreq 0 success
[    23.091] Disable CRTC 0 success
[    23.091] Set CRTC 0 Source success
[    23.091] Mode 1360x768 - 1776 798 6
[    23.091] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    23.091] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    23.091] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    23.101] Picked PLL 0
[    23.101] before 8475
[    23.101] after 8475
[    23.101] best_freq: 84857
[    23.101] best_feedback_div: 88
[    23.101] best_frac_feedback_div: 0
[    23.101] best_ref_div: 2
[    23.101] best_post_div: 14
[    23.101] (II) RADEON(0): crtc(0) Clock: mode 84750, PLL 848570
[    23.101] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x58(88), fracfbdiv 0, pdiv 14
[    23.104] Set CRTC 0 PLL success
[    23.104] Set CRTC Timing success
[    23.104] Set CRTC 0 Overscan success
[    23.104] Not using RMX
[    23.104] scaler 0 setup success
[    23.104] Set CRTC 0 Source success
[    23.104] crtc 0 YUV disable setup success
[    23.104] Output DAC2 setup success
[    23.104] Output CRT2 enable success
[    23.104] Enable CRTC 0 success
[    23.104] Enable CRTC memreq 0 success
[    23.104] Unblank CRTC 0 success
[    23.104] Blank CRTC 1 success
[    23.104] Disable CRTC memreq 1 success
[    23.104] Disable CRTC 1 success
[    23.104] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.104] (--) RandR disabled
[    23.104] (II) Initializing built-in extension Generic Event Extension
[    23.104] (II) Initializing built-in extension SHAPE
[    23.104] (II) Initializing built-in extension MIT-SHM
[    23.104] (II) Initializing built-in extension XInputExtension
[    23.104] (II) Initializing built-in extension XTEST
[    23.104] (II) Initializing built-in extension BIG-REQUESTS
[    23.104] (II) Initializing built-in extension SYNC
[    23.104] (II) Initializing built-in extension XKEYBOARD
[    23.104] (II) Initializing built-in extension XC-MISC
[    23.104] (II) Initializing built-in extension SECURITY
[    23.104] (II) Initializing built-in extension XINERAMA
[    23.104] (II) Initializing built-in extension XFIXES
[    23.104] (II) Initializing built-in extension RENDER
[    23.104] (II) Initializing built-in extension RANDR
[    23.104] (II) Initializing built-in extension COMPOSITE
[    23.104] (II) Initializing built-in extension DAMAGE
[    23.104] (II) SELinux: Disabled on system
[    23.113] (II) AIGLX: Screen 0 is not DRI2 capable
[    23.113] (II) AIGLX: Screen 0 is not DRI capable
[    23.339] (II) AIGLX: Loaded and initialized swrast
[    23.339] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.352] (II) RADEON(0): Setting screen physical size to 359 x 203
[    24.021] (II) config/udev: Adding input device Power Button (/dev/input/event4)
[    24.021] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.021] (II) LoadModule: "evdev"
[    24.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.046] (II) Module evdev: vendor="X.Org Foundation"
[    24.046] 	compiled for 1.12.1, module version = 2.7.0
[    24.046] 	Module class: X.Org XInput Driver
[    24.046] 	ABI class: X.Org XInput driver, version 16.0
[    24.046] (II) Using input driver 'evdev' for 'Power Button'
[    24.046] (**) Power Button: always reports core events
[    24.046] (**) evdev: Power Button: Device: "/dev/input/event4"
[    24.046] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.046] (--) evdev: Power Button: Found keys
[    24.046] (II) evdev: Power Button: Configuring as keyboard
[    24.046] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event4"
[    24.046] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    24.046] (**) Option "xkb_rules" "evdev"
[    24.046] (**) Option "xkb_model" "pc105"
[    24.046] (**) Option "xkb_layout" "de"
[    24.046] (**) Option "xkb_variant" "nodeadkeys"
[    24.268] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    24.268] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.268] (II) Using input driver 'evdev' for 'Power Button'
[    24.268] (**) Power Button: always reports core events
[    24.268] (**) evdev: Power Button: Device: "/dev/input/event3"
[    24.268] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.268] (--) evdev: Power Button: Found keys
[    24.268] (II) evdev: Power Button: Configuring as keyboard
[    24.268] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3/event3"
[    24.268] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    24.268] (**) Option "xkb_rules" "evdev"
[    24.268] (**) Option "xkb_model" "pc105"
[    24.268] (**) Option "xkb_layout" "de"
[    24.268] (**) Option "xkb_variant" "nodeadkeys"
[    24.270] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event0)
[    24.270] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    24.270] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    24.270] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    24.270] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event0"
[    24.270] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc050
[    24.270] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    24.270] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    24.270] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    24.270] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    24.270] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    24.270] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    24.270] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    24.270] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.270] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input0/event0"
[    24.270] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[    24.271] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    24.271] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    24.271] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    24.271] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    24.271] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    24.272] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    24.272] (II) No input driver specified, ignoring this device.
[    24.272] (II) This device may have been added with another device file.
[    24.273] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event1)
[    24.273] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    24.273] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    24.273] (**) Microsoft Wired Keyboard 600: always reports core events
[    24.273] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event1"
[    24.273] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x7f8
[    24.273] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    24.273] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    24.273] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input1/event1"
[    24.273] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 9)
[    24.273] (**) Option "xkb_rules" "evdev"
[    24.273] (**) Option "xkb_model" "pc105"
[    24.273] (**) Option "xkb_layout" "de"
[    24.273] (**) Option "xkb_variant" "nodeadkeys"
[    24.275] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event2)
[    24.275] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    24.275] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    24.275] (**) Microsoft Wired Keyboard 600: always reports core events
[    24.275] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event2"
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x7f8
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Found 1 mouse buttons
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Found scroll wheel(s)
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Found relative axes
[    24.275] (II) evdev: Microsoft Wired Keyboard 600: Forcing relative x/y axes to exist.
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Found absolute axes
[    24.275] (II) evdev: Microsoft Wired Keyboard 600: Forcing absolute x/y axes to exist.
[    24.275] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    24.275] (II) evdev: Microsoft Wired Keyboard 600: Configuring as mouse
[    24.275] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    24.275] (II) evdev: Microsoft Wired Keyboard 600: Adding scrollwheel support
[    24.275] (**) evdev: Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[    24.275] (**) evdev: Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.276] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input2/event2"
[    24.276] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 10)
[    24.276] (**) Option "xkb_rules" "evdev"
[    24.276] (**) Option "xkb_model" "pc105"
[    24.276] (**) Option "xkb_layout" "de"
[    24.276] (**) Option "xkb_variant" "nodeadkeys"
[    24.276] (II) evdev: Microsoft Wired Keyboard 600: initialized for relative axes.
[    24.276] (WW) evdev: Microsoft Wired Keyboard 600: ignoring absolute axes.
[    24.277] (**) Microsoft Wired Keyboard 600: (accel) keeping acceleration scheme 1
[    24.277] (**) Microsoft Wired Keyboard 600: (accel) acceleration profile 0
[    24.277] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[    24.277] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
[    24.278] (II) config/udev: Adding input device PC Speaker (/dev/input/event5)
[    24.278] (II) No input driver specified, ignoring this device.
[    24.278] (II) This device may have been added with another device file.
[   124.598] Dac detection success
[   124.598] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   124.598] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   124.604] Dac detection success
[   124.604] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   124.605] Unhandled monitor type 0
[   124.807] Dac detection success
[   124.807] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   124.807] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   124.817] Dac detection success
[   124.817] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   124.817] Unhandled monitor type 0
[   134.673] Dac detection success
[   134.673] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   134.673] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   134.683] Dac detection success
[   134.683] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   134.683] Unhandled monitor type 0
[   148.257] Dac detection success
[   148.257] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   148.257] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   148.263] Dac detection success
[   148.263] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   148.263] Unhandled monitor type 0
[   149.774] Dac detection success
[   149.774] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   149.774] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   149.782] Dac detection success
[   149.782] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   149.782] Unhandled monitor type 0
[   151.993] Dac detection success
[   151.993] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   151.993] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[   152.000] Dac detection success
[   152.000] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   152.000] Unhandled monitor type 0

```

Let me note that I use a xorg.conf file in my Debian installation. Its content is:

```
Section "Monitor"
        Identifier   "VGA-0"
        Option "Enable" "true"
        Option "PreferredMode" "1360x768"
EndSection
```

The output of xrandr is:

```
root@samba:~# su jrad
jrad@samba:/root$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8*+
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   680x384       119.6    119.9  
   576x432       120.1  
   512x384       120.0  
   400x300       120.6  
   320x240       120.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
jrad@samba:/root$ 


```

> The Xorg log will confirm a working video mode & the FOSS driver etc.
We can apply that video mode to ubuntu setup.

That's a good idea.

But let me add that the resolution 1360x768 in which Debian is running is not offered to me if I enter the grub shell of my Ubuntu Studio installation and then enter "vbeinfo" at the grub prompt.

Best regards,

nfidia

---

### Post by blm-ubunet on 2015-07-26
I think "vbeinfo" only reports standardizes vesa video modes; maybe 1360x768 is not supported.
Does it really matter what mode is used in start-up, splash screen hides it normally..

You should not need to run the first (2) lines, the 3rd line should be enough:
In Ubuntu (logged into X server desktop GUI & terminal)
```
xrandr --newmode "1360x768x59.8"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA-0 "1360x768x59.8"
xrandr --output VGA-0 --mode "1360x768x59.8"
xrandr -prop
```
What video mode does your TV report ?

FYI:
Xrandr screen names must depend on the video driver..
On my intel netbook the screen identifier has to be "VGA0" or "VGA1
The above video mode is stock std mode from:
```
cvt 1360 768 60
```
a better choice for a DFP display is below but your TV may not like it.
```
cvt -r 1360 768 60
```

---

### Post by nfidia on 2015-07-26
Hi blm-ubunet,

When I run "xrandr --output VGA-0 --mode "1360x768x59.8"", then I get the following output:

```
jrad@music:~/Schreibtisch$ xrandr --output VGA-0 --mode "1360x768x59.8"
xrandr: cannot find mode 1360x768x59.8
jrad@music:~/Schreibtisch$
```

So I had to execute all the commands that you posted in your last post. And the resolution indeed gets changed, and the display area is equal to the monitor area. So this is good. But there is something wrong in this new resolution with regard to the display of letters (f.e. below programm icons, or in the menus). The letters look somehow "dirty", I do not know how to explain this better.

Maybe this phenomenon would disappear if I could specify the colour depth for 1360x768x59.8, but according to me the programme xrandr does not offer a switch for defining the colour depth. 

> What video mode does your TV report ?

The product information section in the manual of my TV screen does not provide information about video modes, it only lists different possible resolutions and the respective Hz numbers in the subsection "Computer formats". In the subsection "Video formats" it lists different resolutions and the refresh rates, like "480i - 60 Hz" or "576p - 60 Hz", but I do not think you mean this.

> FYI:
Xrandr screen names must depend on the video driver..
On my intel netbook the screen identifier has to be "VGA0" or "VGA1
The above video mode is stock std mode from:
```
cvt 1360 768 60
```
a better choice for a DFP display is below but your TV may not like it.
```
cvt -r 1360 768 60
```

Currently I am not keen on applying these commands, because I do not know if they could destroy my TV screen. Are these commands harmless to my TV screen?

Best regards,

nfidia

---

### Post by nfidia on 2015-07-26
Something strange just had happened:

During the second last boot of Ubuntu Studio the GUI was again displayed as described in my very first post of this thread: i.e. the display area was moved to the left, I could not see the start button in the upper right corner, there was a black area between the right edge of the display area and the right edge of my TV screen, and the resolution was changed, it seemed to be 1024x768 pixels.

Although I did not change anything with regard to the configuration of the driver and the resolution. Although I already had changed the display settings for Ubuntu Studio via the adjustments menu of my TV screen several days ago, as described here before.

After the following boot everything was fine again with regard to the display by my TV screen.

Strange.

---

### Post by blm-ubunet on 2015-07-26
I'm sure its your TVs prescaler.. probably a certain sequence of video modes (& timings) triggers some overscan/video mode response.

I'm sure your TV can report the incoming video mode (my old Philips CRT can).
And be very surprised if you can't find a (setup/system) menu option to defeat the overscan on PC connection.

The "cvt" command is just a calculator..
I'm sure those video modes will do no harm; you have a digital prescaler between the PC & TV panel.
The days of analogue PLLs & CRTs are long passed.

The dirtyness of the text etc indicates that you do not get one-one direct pixel mapping but the video mode is possibly close to native (bad aliasing).

You didn't post the output of "xrandr".
Can you do this before adding/changing any video modes?

The video mode you tried previous should have been built-in but with a slightly different name.
xrandr --output VGA-0 --mode "1360x768" or
xrandr --output VGA-0 --mode "1360x768_60"
xrandr will list them..

A possibly better video mode is
```
cvt -r 1366 768
Modeline "1368x768R"   72.25  1368 1416 1448 1528  768 771 781 790 +hsync -vsync
```
Maybe that will reduce the aliasing.

---

### Post by nfidia on 2015-07-27
Hi blm-ubunet,

> **blm-ubunet said:**
> I'm sure its your TVs prescaler.. probably a certain sequence of video modes (& timings) triggers some overscan/video mode response.

I'm sure your TV can report the incoming video mode (my old Philips CRT can).
And be very surprised if you can't find a (setup/system) menu option to defeat the overscan on PC connection.

The "cvt" command is just a calculator..
I'm sure those video modes will do no harm; you have a digital prescaler between the PC & TV panel.
The days of analogue PLLs & CRTs are long passed.

The dirtyness of the text etc indicates that you do not get one-one direct pixel mapping but the video mode is possibly close to native (bad aliasing).

Thanks for the information.

> You didn't post the output of "xrandr".
Can you do this before adding/changing any video modes?

Yes of course I can do that.

But let me say that I am not happy with the resolution of 1360x768. At least in Ubuntu, in Debian its fine. As I found out in the meantime, the resolution of 1360x768 is too big for the means of a Ubuntu Studio installation, i.e. music production (windows, icons, characters are too big for this). In Ubuntu Studio I am happy with the resolution that Ubuntu Studio currently offers me by default. This default resolution seems to be 1920x1080, and I would like to keep this resolution.

The default displayed resolution seems to be 1920x1080, if one looks at the Xorg.0.log file:

```

[...]
[    33.505] (II) RADEON(0): Printing probed modes for output VGA-0
[    33.505] (II) RADEON(0): Modeline "_1920x1080_"x59.9  138.50  1920 1968 2000 2080  1080 1082 1087 1111 -hsync +vsync (66.6 kHz eP)
[    33.505] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.505] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 776 798 -hsync -vsync (47.7 kHz e)
[    33.505] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.505] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.505] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[...]

```

> The video mode you tried previous should have been built-in but with a slightly different name.
xrandr --output VGA-0 --mode "1360x768" or
xrandr --output VGA-0 --mode "1360x768_60"
xrandr will list them..

A possibly better video mode is
```
cvt -r 1366 768
Modeline "1368x768R"   72.25  1368 1416 1448 1528  768 771 781 790 +hsync -vsync
```
Maybe that will reduce the aliasing.

Thank you, but as I wrote above, I would like to keep the resolution of 1920x1080.

I do not know how to proceed with this thread. My problem is that if I want to see Ubuntu boot messages during boot, then the display shows the behaviour which I described in my first post of this thread.

Best regards,

nfidia

---

### Post by blm-ubunet on 2015-07-27
Looking back at old posts I noticed in the debian Xorg.0.log:
> Not using default mode "1360x768" (monitor doesn't support reduced blanking)
Assuming (dangerous) that comment applies to all your TV modes then any video modes calculated with "cvt" should not use "-r" option.

Note that the modeline that you highlighted:-- 
--  is a reduced vertical blanking timing (cvt -r)
-- is  not the default
-- does not imply it is used for the desktop

If you want to try 1920x1080 then use xrandr with the probed/parsed/validated modelines as listed by "xrandr".
```
xrandr --output VGA-0 --mode "1920x1080"
```

---

### Post by nfidia on 2015-07-27
Hi blm-ubunet,

This is the information which xrandr gives having started Ubuntu Studio, not having changed anything with regard to the resolution:

```
jrad@music:~/Schreibtisch$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x54)  138.5MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1082 end 1087 total 1111           clock   59.9Hz
jrad@music:~/Schreibtisch$ 

```

So 1920x1080 is the standard resolution in my Ubuntu installation. The resolution definition in my /etc/default/grub file is ignored or gets changed to 1920x1080 during the boot process:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=VGA-0:1280x960-32@60"
```

But 1920x1080 is okay for me, at least when running Ubuntu Studio.

Regards,

nfidia

---

