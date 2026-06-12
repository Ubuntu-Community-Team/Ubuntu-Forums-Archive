---
title: "Cannot build .deb"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by akniss on 2006-06-10
When following the instructions at the following thread to get ATI drivers installed,
[HTML]http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26[/HTML]

I get stuck during the steip where it tells me to build the .deb packages with the command:
```
./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper

```


Below is the terminal output from the failed build.  Could someone help me figure out why this will not work for me?

```
akniss@Dell-Laptop:~$ ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.24.8.............................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.24.8-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
make: Entering directory `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx/debian/fglrx.default ]; then \
          mv /tmp/fglrx/debian/fglrx.default /tmp/fglrx/debian/fglrx; \
        fi
dh_testdir
dh_testdir
make: Leaving directory `/tmp/fglrx'
 fakeroot debian/rules binary
make: Entering directory `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx/debian/fglrx.default ]; then \
          mv /tmp/fglrx/debian/fglrx.default /tmp/fglrx/debian/fglrx; \
        fi
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/dri \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                usr/share/fglrx/diversions \
                etc/acpi \
                etc/acpi/events \
                etc/default
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
                usr/bin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pfglrx-sources \
                usr/src
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "etc/fglrx*"                "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib/*.a"   "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
# Kernel source package
dh_install -pfglrx-kernel-source \
                lib/modules/fglrx/build_mod/*.c            \
                lib/modules/fglrx/build_mod/*.h            \
                lib/modules/fglrx/build_mod/*.sh           \
                lib/modules/fglrx/build_mod/lib*           \
                lib/modules/fglrx/build_mod/2.6.x/Makefile \
                usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source  \
                debian/copyright        \
                debian/compat           \
                module/rules            \
                module/control.template \
                module/dirs.template    \
                module/postinst         \
                usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
         && chown -R root:src modules \
         && tar -c modules | bzip2 > fglrx.tar.bz2 \
         && rm -rf modules)
# control panel package
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pixmaps"
dh_install -A -pfglrx-control "debian/fireglcontrol.desktop"      "usr/share/gnome/apps"
dh_install -A -pfglrx-control "debian/fireglcontrol.kdelnk"       "usr/share/applnk"
# control panel source package
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_gamma.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_pp.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/dri/atiogl_a_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/drivers/fglrx_drv.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fgl_glxgears
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrxinfo
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/aticonfig
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libaticonfig.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_dm.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_gamma.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_pp.a
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/fglrx-control/usr/bin/fireglcontrolpanel
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libgcc_s.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx'
~/fglrx-install
Removing temporary directory: fglrx-install
```

---

### Post by antares2001 on 2006-08-02
Same problem here! Yet solved?

---

### Post by akniss on 2006-08-12
> **antares2001 said:**
> Same problem here! Yet solved?

The problem trying to install the .deb has not been solved... however I stopped looking about two weeks ago when my ATI 3d started working 'spontaneously' again...  I will never buy another computer with ATI hardware....

---

