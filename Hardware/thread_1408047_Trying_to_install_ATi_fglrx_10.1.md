---
title: "Trying to install ATi fglrx 10.1"
date: 2010-02-15
forum: Hardware
---

### Post by JerichoKru on 2010-02-15
Using the guide here > [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) (since it never failed me before), I get to the building of the deb files, only to get this:

```
jericho@JerichoXubuntuNote  ~/Downloads/ATI  >  sh ati-driver-installer-10-1-x86.x86_64.run --buildpkg Ubuntu/karmic
Created directory fglrx-install.hmCKYJ
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.69................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
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
dpkg-buildpackage: source version 2:8.690-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
			-e "s|#LIBDIR#|lib64|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.690|"   \
			-e "s|#XARCH#|x740_64a|"   \
			-e "s|#ARCH#|x86_64|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
		arch/x86_64/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 fakeroot debian/rules binary
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
			-e "s|#LIBDIR#|lib64|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.690|"   \
			-e "s|#XARCH#|x740_64a|"   \
			-e "s|#ARCH#|x86_64|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
		arch/x86_64/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
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
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
			debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
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
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
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
make: *** wait: No child processes.  Stop.
make: *** Waiting for unfinished jobs....
make: *** wait: No child processes.  Stop.
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.690-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
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
			-e "s|#LIBDIR#|lib64|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.690|"   \
			-e "s|#XARCH#|x740_64a|"   \
			-e "s|#ARCH#|x86_64|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
		arch/x86_64/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
		debian/modaliases/fglrx-modules.alias.override
 fakeroot debian/rules binary
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
			-e "s|#LIBDIR#|lib64|"       \
			-e "s|#DRIDIR#|usr/lib|"       \
			-e "s|#CVERSION#|8.690|"   \
			-e "s|#XARCH#|x740_64a|"   \
			-e "s|#ARCH#|x86_64|"   \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
		arch/x86_64/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
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
#driver package
dh_install -XlibAMD -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "arch/x86/usr/lib/*"                     "usr/lib32"
dh_installdirs -pxorg-driver-fglrx "usr/lib32/fglrx"
for i in \
			debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib32/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pxorg-driver-fglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
for i in \
			debian/xorg-driver-fglrx/usr/bin/atiode \
			debian/xorg-driver-fglrx/usr/sbin/amdnotifyui \
			debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so \
			debian/xorg-driver-fglrx/usr/lib/libGL.so.* \
			; do execstack -q $i; execstack -c $i; done
- debian/xorg-driver-fglrx/usr/bin/atiode
- debian/xorg-driver-fglrx/usr/sbin/amdnotifyui
- debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
- debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
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
execstack -c debian/fglrx-amdcccle/usr/bin/amdcccle
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
dh_install -plibamdxvba1 "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
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
dpkg-shlibdeps: warning: symbol dlopen used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlerror used by debian/xorg-driver-fglrx/usr/lib/libXvBAW.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetGeometry used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XSetErrorHandler used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlclose used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XMaxRequestSize used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCreateGC used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeFontInfo used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: couldn't find library libatiuki.so.1 needed by debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so (ELF format: 'elf64-x86-64'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.hmCKYJ

```

I'm finding it difficult to find out what's wrong.

---

### Post by JerichoKru on 2010-02-16
No one?  I can't even build for jaunty.  It just errors out the same way as above.

---

### Post by BobDoLe on 2010-03-07
bump

---

