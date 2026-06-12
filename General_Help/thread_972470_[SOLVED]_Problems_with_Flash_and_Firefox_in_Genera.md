---
title: "[SOLVED] Problems with Flash and Firefox in General"
date: 2008-11-05
forum: General Help
---

### Post by mfmbcpman on 2008-11-05
Firefox is driving me crazy with 8.1 Intrepid. I absolutely cannot get Flash to work. I've searched through many thread with no solution. Also, none of my bookmarks are being saved after I quit out. Currently I have adobe-flashplugin, ubuntu-restricted-extras, and swfdec-mozilla installed in terms of flash packages. Help please?

---

### Post by aysiu on 2008-11-05
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
sudo updatedb
locate flash
cat /etc/lsb-release
uname -m
dpkg -s flashplugin-nonfree
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
``` That first command may take a few minutes to execute. Be patient.

For the bookmarks not being saved, close Firefox completely, then paste this command into the terminal: ```
sudo chown -R $USER:$USER ~/.mozilla
``` and then start Firefox again.

---

### Post by mfmbcpman on 2008-11-05
Bookmarks are working again. Here's the output of those commands.

```
michael@michael-laptop:~$ sudo updatedb
michael@michael-laptop:~$ locate flash
/etc/alternatives/firefox-flashplugin
/etc/alternatives/iceape-flashplugin
/etc/alternatives/iceweasel-flashplugin
/etc/alternatives/midbrowser-flashplugin
/etc/alternatives/mozilla-flashplugin
/etc/alternatives/xulrunner-addons-flashplugin
/etc/alternatives/xulrunner-flashplugin
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/usr/bin/btcflash
/usr/bin/ppmflash
/usr/lib/adobe-flashplugin
/usr/lib/flashplugin-nonfree-extrasound
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.py
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.py
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/flashwin.pyc
/usr/lib/xulrunner/libflashsupport.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/adobe-flashplugin
/usr/share/doc/flashplugin-nonfree-extrasound
/usr/share/doc/adobe-flashplugin/changelog.Debian.gz
/usr/share/doc/adobe-flashplugin/copyright
/usr/share/doc/flashplugin-nonfree-extrasound/README
/usr/share/doc/flashplugin-nonfree-extrasound/changelog.Debian.gz
/usr/share/doc/flashplugin-nonfree-extrasound/copyright
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/128x128/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/16x16/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/22x22/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/32x32/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/48x48/devices/compact_flash_unmount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_mount.png
/usr/share/icons/crystalsvg/64x64/devices/compact_flash_unmount.png
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/icons/oxygen/128x128/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/128x128/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/128x128/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/128x128/devices/media-flash.png
/usr/share/icons/oxygen/16x16/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/16x16/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/16x16/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/16x16/devices/media-flash.png
/usr/share/icons/oxygen/22x22/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/22x22/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/22x22/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/22x22/devices/media-flash.png
/usr/share/icons/oxygen/32x32/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/32x32/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/32x32/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/32x32/devices/media-flash.png
/usr/share/icons/oxygen/48x48/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/48x48/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/48x48/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/48x48/devices/media-flash.png
/usr/share/icons/oxygen/64x64/devices/media-flash-memory-stick.png
/usr/share/icons/oxygen/64x64/devices/media-flash-sd-mmc.png
/usr/share/icons/oxygen/64x64/devices/media-flash-smart-media.png
/usr/share/icons/oxygen/64x64/devices/media-flash.png
/usr/share/man/man1/ppmflash.1.gz
/usr/share/man/man3/flash.3ncurses.gz
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/mimelnk/application/x-shockwave-flash.desktop
/usr/share/vlc/http/flash.html
/usr/share/vlc/lua/http/flash.html
/usr/src/linux-headers-2.6.27-7/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.27-7/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.27-7/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.27-7/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/mtd/scx200/docflash.h
/var/cache/apt/archives/adobe-flashplugin_10.0.12.36-1intrepid2_i386.deb
/var/cache/apt/archives/flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb
/var/cache/apt/archives/flashplugin-nonfree_10.0.12.36ubuntu1_i386.deb
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/alternatives/iceape-flashplugin
/var/lib/dpkg/alternatives/iceweasel-flashplugin
/var/lib/dpkg/alternatives/midbrowser-flashplugin
/var/lib/dpkg/alternatives/mozilla-flashplugin
/var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
/var/lib/dpkg/alternatives/xulrunner-flashplugin
/var/lib/dpkg/info/adobe-flashplugin.list
/var/lib/dpkg/info/adobe-flashplugin.md5sums
/var/lib/dpkg/info/adobe-flashplugin.postinst
/var/lib/dpkg/info/adobe-flashplugin.prerm
/var/lib/dpkg/info/flashplugin-nonfree-extrasound.list
/var/lib/dpkg/info/flashplugin-nonfree-extrasound.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.postrm
michael@michael-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
michael@michael-laptop:~$ uname -m
i686
michael@michael-laptop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: deinstall ok config-files
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 10.0.12.36ubuntu1
Config-Version: 10.0.12.36ubuntu1
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), libflashsupport, xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player (http://www.adobe.com)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
michael@michael-laptop:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 296
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.8.0-0ubuntu1
Replaces: swf-player
Provides: swf-player
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.1.3), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.1), liboil0.3 (>= 0.3.1), libpango1.0-0 (>= 1.21.6), libswfdec-0.8-0, zlib1g (>= 1:1.1.4)
Suggests: ubufox
Conflicts: swf-player
Description: Mozilla plugin for SWF files (Macromedia Flash)
 A GTK+ and swfdec based Mozilla plugin for SWF files,
 commonly known as Macromedia Flash animations.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: GNOME SWF player (http://swfdec.freedesktop.org/)
Npp-File: libswfdecmozilla.so
Npp-Mimetype: application/x-shockwave-flash, application/futuresplash
Npp-Name: Swfdec SWF player
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>
michael@michael-laptop:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

---

### Post by blackraven36 on 2008-11-05
Adobe has identified a problem with flash and Firefox 3, and the next version should fix the problem (If its not out already), I would try to update the version of Flash in addition to the solutions given by other people

---

### Post by aysiu on 2008-11-05
You know it may be something as simple as removing SWFdec: ```
sudo apt-get remove swfdec-mozilla && sudo apt-get install --reinstall flashplugin-nonfree
```

---

### Post by mfmbcpman on 2008-11-06
> **aysiu said:**
> You know it may be something as simple as removing SWFdec: ```
sudo apt-get remove swfdec-mozilla && sudo apt-get install --reinstall flashplugin-nonfree
```

You are awesome. Thank you for the help.

---

### Post by michaelzap on 2008-11-06
> **blackraven36 said:**
> Adobe has identified a problem with flash and Firefox 3, and the next version should fix the problem (If its not out already), I would try to update the version of Flash in addition to the solutions given by other people

Can you provide a link for more info on this? I'm having a terrible time since I upgraded to 8.10, and I suspect that Flash may be the culprit. The latest version that I can find on the Adobe site is the same as what I have now via Synaptic.

---

### Post by Brendt2 on 2008-11-06
I too have recently upgraded and have run into numerous problems with my upgrade path to 8.10 which has caused me much strife!

It appears that Flash 10 has installed successfully but Firefox does not seem to recognized it.  I am using VMs now and am very much in a pickle!

---

### Post by mikedetch on 2008-11-07
Hello, yes I am a newbie to Ubuntu, but I work a lot with HPux. I  have the same problem with Firefox and Adobe Flash. I have an AMD 64 bit processor and installed the 64 bit version of Ubuntu, don't know if that adds an extra twist or not.  I attempted to follow other posted threads on how to fix this, and have most likely made the problem worse by installing various libraries, etc.

I have captured the same queries.  I will be most thankful for any help in untying this knot.



mike@StevieRay:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
mike@StevieRay:~$ sudo updatedb
[sudo] password for mike: 
mike@StevieRay:~$ locate libflash
/home/mike/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so
mike@StevieRay:~$ uname -m
x86_64
mike@StevieRay:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
mike@StevieRay:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: purge ok not-installed
Priority: optional
Section: contrib/web
mike@StevieRay:~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: purge ok not-installed
Priority: optional
Section: utils
mike@StevieRay:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: purge ok not-installed
Priority: optional
Section: utils
mike@StevieRay:~$ locate libflash
/home/mike/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so

---

### Post by a_salieri on 2008-11-27
Hi, y'all.

I'm a recent convert to Ubuntu, and have installed 8.10 (Intrepid Ibex).

I cannot view flash on firefox. I have tried everything I have seen on the posts and all.

I have scoured the net for solution and even where it has worked for others, it doesn't seem to work for me.

I'd really appreciate any and all the help you can offer - start from scratch if you have to.

Thanks y'all in advance.

---

