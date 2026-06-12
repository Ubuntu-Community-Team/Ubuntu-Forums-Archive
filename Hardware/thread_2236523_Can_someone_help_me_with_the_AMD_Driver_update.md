---
title: "Can someone help me with the AMD Driver update"
date: 2014-07-27
forum: Hardware
---

### Post by andrea37 on 2014-07-27
Hi, all. I'm using ubuntu 14.04.
I've to update my AMD (ATI) video card driver with the driver downloaded from the AMD web site.
Now I'm using the proprietary drive that I've choose  in the software update, but this driver is quite old so I'm trying to update it.

I've red this page:
[http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)
It say that I've to uninstall the current driver first.
I've try to uninstall with these commands: "[COLOR=#000000][FONT=Calibri]sudo sh amd-driver-installer-x86.x86_64.run --uninstall"     "[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]sudo sh /usr/share/ati/amd-uninstall.sh" [/FONT][/COLOR] but these file don't exist. Then the page say to try to uninstall with the package manager and I've try with software center but I don't found none, looking of "ati" or "amd".

Then I've tried to make a ubuntu package installer (since is there this option in the ati installer and I prefer to install it in this way), but I get an error and the log file say this:
```
Package build failed!Package build utility output:
Cleaning in directory .
dpkg-checkbuilddeps: Unmet build dependencies: dh-modaliases xserver-xorg-dev (>= 2:1.10.0) | xserver-xorg-dev-lts-quantal | xserver-xorg-dev-lts-raring | xserver-xorg-dev-lts-saucy execstack
debuild: fatal error at line 1328:
You do not appear to have all build dependencies properly met.
You can use mk-build-deps to generate a dummy package which
Depends on all the required packages, or you can install them
manually using dpkg or apt using the error messages just above
this message.
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.100-0ubuntu1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.dxhsR6
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|14.100|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCOTHERARCH#|x86|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# Generate the xserver ABI dependencies
cat debian/substvars >> debian/fglrx.substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Cleaning in directory .
dpkg-checkbuilddeps: Unmet build dependencies: dh-modaliases xserver-xorg-dev (>= 2:1.10.0) | xserver-xorg-dev-lts-quantal | xserver-xorg-dev-lts-raring | xserver-xorg-dev-lts-saucy execstack
debuild: fatal error at line 1328:
You do not appear to have all build dependencies properly met.
You can use mk-build-deps to generate a dummy package which
Depends on all the required packages, or you can install them
manually using dpkg or apt using the error messages just above
this message.
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.100-0ubuntu1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.brdkCc
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|14.100|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCOTHERARCH#|x86|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
# Generate the xserver ABI dependencies
cat debian/substvars >> debian/fglrx.substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/*libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
/bin/sh: 4: execstack: not found
make: *** [binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/trusty
```

how can I do? 

Then an other question is: 
How can I use pc when I will uninstall video card driver  (I will be without video driver!!)  to install the new driver?

Thanks

---

### Post by Yellow Pasque on 2014-07-27
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

> How can I use pc when I will uninstall video card driver (I will be without video driver!!) to install the new driver?
It will still be loaded in RAM until you reboot.

---

