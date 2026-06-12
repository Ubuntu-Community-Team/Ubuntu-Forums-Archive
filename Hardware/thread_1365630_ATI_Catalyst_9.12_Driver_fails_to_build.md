---
title: "ATI Catalyst 9.12 Driver fails to build"
date: 2009-12-27
forum: Hardware
---

### Post by Hoshikage on 2009-12-27
Attempting to build the Catalyst 9.12 driver for the Radeon HD3450, Cannot figure out at all why it keeps failing. 

```
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.681.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
[31m ATI Technologies Linux Driver Installer/Packager [0m
==================================================
Generating package: Ubuntu/karmic
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.681-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: couldn't find library libQtGui.so.4 needed by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui (ELF format: 'elf32-i386'; RPATH: '/usr/share/ati/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.681-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: couldn't find library libQtGui.so.4 needed by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui (ELF format: 'elf32-i386'; RPATH: '/usr/share/ati/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.681-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: couldn't find library libQtGui.so.4 needed by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui (ELF format: 'elf32-i386'; RPATH: '/usr/share/ati/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.681-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
test -x debian/rules
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 debian/rules binary
test -x debian/rules
dh_testroot
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 xorg-driver-fglrx.install \
			 xorg-driver-fglrx-dev.install \
			 fglrx-kernel-source.install \
			 fglrx-amdcccle.install \
			 libamdxvba1.install \
			 overrides/fglrx-kernel-source; do \
		sed -e "s|#XMODDIR#|usr/lib/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#DRIDIR32#|usr/lib32|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.681|"   \
			-e "s|#XARCH#|x740|"   \
			-e "s|#ARCH#|x86|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740/usr/X11R6/lib/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
dh_installdirs -pxorg-driver-fglrx 
dh_installdirs -pxorg-driver-fglrx-dev 
dh_installdirs -pfglrx-kernel-source 
dh_installdirs -pfglrx-amdcccle 
dh_installdirs -pfglrx-modaliases 
dh_installdirs -plibamdxvba1 
dh_installdocs -pxorg-driver-fglrx   
dh_installexamples -pxorg-driver-fglrx 
dh_installman -pxorg-driver-fglrx  
dh_installinfo -pxorg-driver-fglrx  
dh_installmenu -pxorg-driver-fglrx 
dh_installcron -pxorg-driver-fglrx 
dh_installinit -pxorg-driver-fglrx   
dh_installdebconf -pxorg-driver-fglrx 
dh_installemacsen -pxorg-driver-fglrx   
dh_installcatalogs -pxorg-driver-fglrx 
dh_installpam -pxorg-driver-fglrx 
dh_installlogrotate -pxorg-driver-fglrx 
dh_installlogcheck -pxorg-driver-fglrx 
dh_installchangelogs -pxorg-driver-fglrx   
dh_installudev -pxorg-driver-fglrx 
dh_lintian -pxorg-driver-fglrx 
dh_install -pxorg-driver-fglrx  
dh_link -pxorg-driver-fglrx  
dh_installmime -pxorg-driver-fglrx 
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_installdocs -pxorg-driver-fglrx-dev   
dh_installexamples -pxorg-driver-fglrx-dev 
dh_installman -pxorg-driver-fglrx-dev  
dh_installinfo -pxorg-driver-fglrx-dev  
dh_installmenu -pxorg-driver-fglrx-dev 
dh_installcron -pxorg-driver-fglrx-dev 
dh_installinit -pxorg-driver-fglrx-dev   
dh_installdebconf -pxorg-driver-fglrx-dev 
dh_installemacsen -pxorg-driver-fglrx-dev   
dh_installcatalogs -pxorg-driver-fglrx-dev 
dh_installpam -pxorg-driver-fglrx-dev 
dh_installlogrotate -pxorg-driver-fglrx-dev 
dh_installlogcheck -pxorg-driver-fglrx-dev 
dh_installchangelogs -pxorg-driver-fglrx-dev   
dh_installudev -pxorg-driver-fglrx-dev 
dh_lintian -pxorg-driver-fglrx-dev 
dh_install -pxorg-driver-fglrx-dev  
dh_link -pxorg-driver-fglrx-dev  
dh_installmime -pxorg-driver-fglrx-dev 
dh_installdocs -pfglrx-kernel-source   
dh_installexamples -pfglrx-kernel-source 
dh_installman -pfglrx-kernel-source  
dh_installinfo -pfglrx-kernel-source  
dh_installmenu -pfglrx-kernel-source 
dh_installcron -pfglrx-kernel-source 
dh_installinit -pfglrx-kernel-source   
dh_installdebconf -pfglrx-kernel-source 
dh_installemacsen -pfglrx-kernel-source   
dh_installcatalogs -pfglrx-kernel-source 
dh_installpam -pfglrx-kernel-source 
dh_installlogrotate -pfglrx-kernel-source 
dh_installlogcheck -pfglrx-kernel-source 
dh_installchangelogs -pfglrx-kernel-source   
dh_installudev -pfglrx-kernel-source 
dh_lintian -pfglrx-kernel-source 
dh_install -pfglrx-kernel-source  
dh_link -pfglrx-kernel-source  
dh_installmime -pfglrx-kernel-source 
dh_installdocs -pfglrx-amdcccle   
dh_installexamples -pfglrx-amdcccle 
dh_installman -pfglrx-amdcccle  
dh_installinfo -pfglrx-amdcccle  
dh_installmenu -pfglrx-amdcccle 
dh_installcron -pfglrx-amdcccle 
dh_installinit -pfglrx-amdcccle   
dh_installdebconf -pfglrx-amdcccle 
dh_installemacsen -pfglrx-amdcccle   
dh_installcatalogs -pfglrx-amdcccle 
dh_installpam -pfglrx-amdcccle 
dh_installlogrotate -pfglrx-amdcccle 
dh_installlogcheck -pfglrx-amdcccle 
dh_installchangelogs -pfglrx-amdcccle   
dh_installudev -pfglrx-amdcccle 
dh_lintian -pfglrx-amdcccle 
dh_install -pfglrx-amdcccle  
dh_link -pfglrx-amdcccle  
dh_installmime -pfglrx-amdcccle 
dh_installdocs -pfglrx-modaliases   
dh_installexamples -pfglrx-modaliases 
dh_installman -pfglrx-modaliases  
dh_installinfo -pfglrx-modaliases  
dh_installmenu -pfglrx-modaliases 
dh_installcron -pfglrx-modaliases 
dh_installinit -pfglrx-modaliases   
dh_installdebconf -pfglrx-modaliases 
dh_installemacsen -pfglrx-modaliases   
dh_installcatalogs -pfglrx-modaliases 
dh_installpam -pfglrx-modaliases 
dh_installlogrotate -pfglrx-modaliases 
dh_installlogcheck -pfglrx-modaliases 
dh_installchangelogs -pfglrx-modaliases   
dh_installudev -pfglrx-modaliases 
dh_lintian -pfglrx-modaliases 
dh_install -pfglrx-modaliases  
dh_link -pfglrx-modaliases  
dh_installmime -pfglrx-modaliases 
dh_installdocs -plibamdxvba1   
dh_installexamples -plibamdxvba1 
dh_installman -plibamdxvba1  
dh_installinfo -plibamdxvba1  
dh_installmenu -plibamdxvba1 
dh_installcron -plibamdxvba1 
dh_installinit -plibamdxvba1   
dh_installdebconf -plibamdxvba1 
dh_installemacsen -plibamdxvba1   
dh_installcatalogs -plibamdxvba1 
dh_installpam -plibamdxvba1 
dh_installlogrotate -plibamdxvba1 
dh_installlogcheck -plibamdxvba1 
dh_installchangelogs -plibamdxvba1   
dh_installudev -plibamdxvba1 
dh_lintian -plibamdxvba1 
dh_install -plibamdxvba1  
dh_link -plibamdxvba1  
dh_installmime -plibamdxvba1 
dh_strip -pxorg-driver-fglrx  
dh_compress -pxorg-driver-fglrx  
dh_fixperms -pxorg-driver-fglrx  
dh_makeshlibs -pxorg-driver-fglrx  
dh_strip -pxorg-driver-fglrx-dev  
dh_compress -pxorg-driver-fglrx-dev  
dh_fixperms -pxorg-driver-fglrx-dev  
dh_makeshlibs -pxorg-driver-fglrx-dev  
dh_strip -pfglrx-kernel-source  
dh_compress -pfglrx-kernel-source  
dh_fixperms -pfglrx-kernel-source  
dh_makeshlibs -pfglrx-kernel-source  
dh_strip -pfglrx-amdcccle  
dh_compress -pfglrx-amdcccle  
dh_fixperms -pfglrx-amdcccle  
dh_makeshlibs -pfglrx-amdcccle  
dh_strip -pfglrx-modaliases  
dh_compress -pfglrx-modaliases  
dh_fixperms -pfglrx-modaliases  
dh_makeshlibs -pfglrx-modaliases  
dh_strip -plibamdxvba1  
dh_compress -plibamdxvba1  
dh_fixperms -plibamdxvba1  
dh_makeshlibs -plibamdxvba1  
dh_installdeb -pxorg-driver-fglrx 
dh_perl -pxorg-driver-fglrx 
dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: couldn't find library libQtGui.so.4 needed by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui (ELF format: 'elf32-i386'; RPATH: '/usr/share/ati/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.vLJ3wH
```

Is the output I get from attempting to build. 

I would just use the driver provided in Jockey, but I just get a black screen after rebooting and nothing I've done to attempt to fix that has worked.

---

### Post by Hoshikage on 2009-12-27
Got the drivers built. Still having the same problem, which leads me to believe that I need to change something about my xorg.conf.

Current xorg.conf looks like 

```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
 
 
Section "Module"
        Load  "extmod"
        Load  "dbe"
        Load  "xtrap"
        Load  "record"
        Load  "dri"
        Load  "glx"
        Load  "GLcore"
        Load  "freetype"
EndSection
 
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection
 
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
 
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
 
Section "Device"
        Identifier  "Card0"
        Driver      "fglrx"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon HD3450"
        BusID       "PCI:3:0:0"
EndSection
 
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
 
Section "DRI"
        Mode 0666
EndSection
```

---

### Post by MeanEYE on 2009-12-27
I just gave up on ATI moments ago. Nothing seemed to work :/
Can you be more specific for which card are you trying to install these drivers?

---

### Post by Hoshikage on 2009-12-27
I said the Radeon HD 3450. 

If you want manufacturer and such, it's [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131119) card.

---

### Post by adam814 on 2009-12-28
Yeah, I never had luck with any Catalyst version other than 9.4 in Jaunty.  I have a Radeon HD3470 myself.

I've since upgraded to Karmic and dropped fglrx in favor of the open-source radeon driver.  There's still no hardware 3d support, but the 2d acceleration is decent.  With the SKIP_CHECKS=yes environment variable set I'm able to start compiz, but I'm running a mainline 2.6.32 series kernel and using the experimental xorg-edgers ppa.  I haven't been able to get KMS working.

I should mention my attempts with fglrx in Karmic failed dismally leaving the vesa driver in use.  As a disclaimer the xorg-edgers packagers warn of possible breakages since their packages are compiled from as far upstream as possible, but I haven't had any serious issues with either that or the mainline kernel based on those from kernel.ubuntu.com running with an otherwise "stock" Karmic userland.

---

### Post by Hoshikage on 2009-12-28
So I'm screwed for getting Catalyst working then? Any suggestions for a different distro in which I may have better luck?

I've tried out Arch, but left it because of lack of support for the current Catalyst driver. I've also played with Gentoo, spent two days getting that set up, but that was with a nVidia card.

---

### Post by adam814 on 2009-12-28
As I understand it for flgrx to be happy you need a 2.6.30 or older kernel and an xserver version older than 1.6.0.  The odds of having that combination in a modern distro is pretty slim.  If you absolutely must have Catalyst I'm seeing about 3 options:

1) Go with Ubuntu 8.04.1 LTS which if I recall uses xserver 1.5 series and the 2.6.24 kernel or similar release-date distro (Fedora 9 or OpenSUSE 11.0 perhaps).
2) Go with an "enterprise" distro (CentOS is probably the most accessible free one).  I don't like this option because laptop hardware from the last few years may not be recognized.
3) Go with Gentoo or Slackware and build your own.

If I had to pick one I'd try 8.04.1 LTS first as it's still supported for a few more years and with backports enabled you'll still have a fairly up-to-date machine.

P.S. I vaguely remember there being an "xorg downgrades" ppa that would support fglrx.  Good luck.

---

### Post by convivius on 2010-01-18
I saw the same error message you're seeing; installing the libqt4-gui package fixes it. The catalyst release 9.12 should at least build fine... it's still less stable than the radeon driver, though.

For reference, I'm running:
  Hardy (8.04)
  ATI Radeon HD 3870
  # as root
  apt-get install libqt4-core libqt4-gui
  ./ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/8.04
  dpkg -i *deb
Update X conf, restart X, etc.

---

### Post by adam814 on 2010-01-18
That probably works quite nicely on 8.04.  I didn't have any trouble with (compiling, just video playback and Compiz) ATI drivers on Hardy or Intrepid.

---

### Post by ioargento on 2010-01-20
Same problem here 9.10 and Radeon 3200. Any ideas?

---

