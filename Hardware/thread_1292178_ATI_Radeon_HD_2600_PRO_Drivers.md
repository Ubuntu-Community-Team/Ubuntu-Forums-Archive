---
title: "ATI Radeon HD 2600 PRO Drivers?"
date: 2009-10-15
forum: Hardware
---

### Post by sdwrage on 2009-10-15
Hey all,

First post so I guess I will say hello here. Hello! :) Now on to my question. I started using Ubuntu again after a break from it. Even when I did use it, I only had it on my laptop which had a nvidia graphics card on it for about a month. Now I need it on my desktop for web work (I do php but want to dabble in Ruby on Rails a bit) but I have an ATI card in it. The problem I face is the proprietary driver that Ubuntu Hardware Installer suggested slows down my startup, my display properties window (basically locks up) and anything I basically attempt to do. I was wondering if there is an easy to follow guide on an open source driver for my ATI card that might help? Any suggestions will help here.

Thanks

---

### Post by sdwrage on 2009-10-15
bump? :)

---

### Post by sdwrage on 2009-10-20
Anyone got any feedback on this?

---

### Post by BMWDriver on 2009-10-21
Yup, ATI is a bit of a pain in the neck to figure out. But basically, for ATI cards other that recent HD3000 and up, the 9.10 Catalyst drivers will not work. Support stops at Catalyst 9.3. 

However, open drivers work best and have good performance overall. This will also depend on your version of Ubuntu. Open drivers are known as "radeon". Anyhow, if you go over here : [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver"), you ought to do well for a start. 

First, though, you'll have to uninstall the Catalyst drivers, also known as fglrx. I believe this is outlined in the above link. Otherwise, removing fglrx is also described here (this is the link for Jaunty 9.04): [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#HOW_TO_REMOVE_DRIVER]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#HOW_TO_REMOVE_DRIVER")

---

### Post by pete storr on 2009-10-21
Hi, first post 2, how you getting on with the HD 2600 pro?

I have the same problems here with the same card, 

goood luck

pete

---

### Post by Stratis on 2009-11-19
I'm also having problems with mine.

When I log in I can't click on any of the panels or windows (I can navigate the windows with keystrokes but clicking doesn't work).

Dudes!

I just bought this card a few weeks ago expecting it to be better than my old radeon 7500
(Also expecting better Linux support from an Ati card).

---

### Post by andrewthomas on 2010-02-08
I have a 2600 pro and I used the built in *Hardware Drivers* manager in Ubuntu to install the the proprietary fglrx driver. 


[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by neonathon on 2010-02-08
sorry to interrupt, but do any of you know how to post new questions? I searched the whole site and couldn't find it!

---

### Post by andrewthomas on 2010-02-08
there should be a grey new thread button at the top of the page.

---

### Post by Raavea on 2010-09-13
I realise this is an old thread, but I'm having a similar problem with 10.04.
 I'm about to follow this guide;
[http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html)
 Which you guys might find helpful if you still check this thread! I found it by googling for help, so might help someone else.. :)

---

### Post by Yellow Pasque on 2010-09-13
I would prefer this guide since it builds packages (easier removal): [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by Raavea on 2010-09-13
The guide I followed does not seem to have helped at all, so I'll try that one, thanks Temüjin.

EDIT: It's not working. Gah!!
```
$ sh ati-driver-installer-10-8-x86.x86_64.run --buildpkg Ubuntu/lucid
Created directory fglrx-install.0mn6gs
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.762........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/lucid
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.762-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-amdcccle.install \
			 overrides/fglrx; do \
		sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib/fglrx|"       \
			-e "s|#CVERSION#|8.762|"   \
			-e "s|#XARCH#|x750|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x750     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_installdirs -pfglrx
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
			debian/fglrx/usr/lib/fglrx/bin/atiode \
			debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
			debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
			debian/fglrx/usr/lib/fglrx/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
		-type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.k4nH5s/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >	"/tmp/fglrx.k4nH5s/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a
   dh_installexamples -a
   dh_installman -a
   dh_installcatalogs -a
   dh_installcron -a
   dh_installdebconf -a
   dh_installemacsen -a
   dh_installifupdown -a
   dh_installinfo -a
   dh_pysupport -a
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a
   dh_installmime -a
   dh_installmodules -a
   dh_installlogcheck -a
   dh_installlogrotate -a
   dh_installpam -a
   dh_installppp -a
   dh_installudev -a
   dh_installwm -a
   dh_installxfonts -a
   dh_bugfiles -a
   dh_lintian -a
   dh_gconf -a
   dh_icons -a
   dh_perl -a
   dh_usrlocal -a
   dh_link -a
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.k4nH5s'
dh_shlibdeps -l/tmp/fglrx.k4nH5s/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 29 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/libaticaldd.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.k4nH5s'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.762-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-amdcccle.install \
			 overrides/fglrx; do \
		sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib/fglrx|"       \
			-e "s|#CVERSION#|8.762|"   \
			-e "s|#XARCH#|x750|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x750     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_installdirs -pfglrx
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
			debian/fglrx/usr/lib/fglrx/bin/atiode \
			debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
			debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
			debian/fglrx/usr/lib/fglrx/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
		-type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.YNG1Bw/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >	"/tmp/fglrx.YNG1Bw/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a
   dh_installexamples -a
   dh_installman -a
   dh_installcatalogs -a
   dh_installcron -a
   dh_installdebconf -a
   dh_installemacsen -a
   dh_installifupdown -a
   dh_installinfo -a
   dh_pysupport -a
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a
   dh_installmime -a
   dh_installmodules -a
   dh_installlogcheck -a
   dh_installlogrotate -a
   dh_installpam -a
   dh_installppp -a
   dh_installudev -a
   dh_installwm -a
   dh_installxfonts -a
   dh_bugfiles -a
   dh_lintian -a
   dh_gconf -a
   dh_icons -a
   dh_perl -a
   dh_usrlocal -a
   dh_link -a
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.YNG1Bw'
dh_shlibdeps -l/tmp/fglrx.YNG1Bw/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 29 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/libaticaldd.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.YNG1Bw'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.762-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-amdcccle.install \
			 overrides/fglrx; do \
		sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib/fglrx|"       \
			-e "s|#CVERSION#|8.762|"   \
			-e "s|#XARCH#|x750|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x750     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_installdirs -pfglrx
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
			debian/fglrx/usr/lib/fglrx/bin/atiode \
			debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
			debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
			debian/fglrx/usr/lib/fglrx/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
		-type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.gOB0rk/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >	"/tmp/fglrx.gOB0rk/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a
   dh_installexamples -a
   dh_installman -a
   dh_installcatalogs -a
   dh_installcron -a
   dh_installdebconf -a
   dh_installemacsen -a
   dh_installifupdown -a
   dh_installinfo -a
   dh_pysupport -a
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a
   dh_installmime -a
   dh_installmodules -a
   dh_installlogcheck -a
   dh_installlogrotate -a
   dh_installpam -a
   dh_installppp -a
   dh_installudev -a
   dh_installwm -a
   dh_installxfonts -a
   dh_bugfiles -a
   dh_lintian -a
   dh_gconf -a
   dh_icons -a
   dh_perl -a
   dh_usrlocal -a
   dh_link -a
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.gOB0rk'
dh_shlibdeps -l/tmp/fglrx.gOB0rk/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 19 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 29 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/libaticaldd.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.gOB0rk'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.0mn6gs
```

---

