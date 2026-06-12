---
title: "Error installing fglrx driver on Xenial"
date: 2016-03-01
forum: Hardware
---

### Post by glenn_morrissey2 on 2016-03-01
Hi

I have downloaded a fglrx driver for my ati video driver.

```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]

```

radeon-crimson-15.12-15.302-151217a-297685e.zip

I have installed the necessary dependencies with apt.
I ran the installer and received the following error:

```

geek@geek-ThinkPad-T400:~/Downloads/fglrx-15.302$ cd /usr/share/ati
geek@geek-ThinkPad-T400:/usr/share/ati$ ls
fglrx-install.log  LICENSE.TXT
geek@geek-ThinkPad-T400:/usr/share/ati$ cat fg*
NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Check if system has the tools required for Packages Generation.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 296: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:15.302-0ubuntu1
dpkg-buildpackage: source distribution xenial
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.yDgXuf
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
         control \
         dkms.conf \
         fglrx"".install \
         fglrx""-dev.install \
         fglrx""-dev.links \
         fglrx"".dirs \
         fglrx"".links \
         fglrx"".postinst \
         fglrx"".postrm \
         fglrx"".preinst \
         fglrx"".prerm \
         fglrx-amdcccle"".install \
         fglrx-amdcccle"".dirs \
         fglrx""-core.install \
         fglrx""-core.links \
         fglrx""-core.dirs \
         fglrx""-core.postinst \
         fglrx""-core.postrm \
         fglrx""-core.preinst \
         fglrx""-core.prerm \
         overrides/fglrx"" \
         overrides/fglrx""-dev \
         overrides/fglrx""-core \
         overrides/fglrx-amdcccle""; do \
    sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
        -e "s|#LIBDIR#|usr/lib|g" \
        -e "s|#LIBDIR32#|usr/lib32|g" \
        -e "s|#BINDIR#|usr/bin|g" \
        -e "s|#SBINDIR#|usr/sbin|g" \
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
        -e "s|#DRIVERNAME#|fglrx""|g" \
        -e "s|#MODULENAME#|fglrx|g" \
        -e "s|#DRIVERDIRNAME#|fglrx|g" \
        -e "s|#DRIVERDEVNAME#|fglrx""-dev|g" \
        -e "s|#DRIVERSRCNAME#|fglrx-installer|g" \
        -e "s|#DRIVERCORENAME#|fglrx""-core|g" \
        -e "s|#FLAVOUR#|""|g" \
        -e "s|#DRIVERCTRLNAME#|fglrx-amdcccle""|g" \
        -e "s|#INCLUDEDIR#|usr/include|g" \
        -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
        -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
        -e "s|#PXDIR#|usr/lib/pxpress|g" \
        -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
        -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
        -e "s|#PXDIRNAME#|pxpress|g" \
        -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
        -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
        -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
        -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
        -e "s|#COREDIRNAME#|fglrx-core|g" \
        -e "s|#COREDIR#|usr/lib/fglrx-core|g" \
        -e "s|#COREDIR32#|usr/lib32/fglrx-core|g" \
        -e "s|#CORELDSOCONF#|usr/lib/fglrx-core/ld.so.conf|g" \
        -e "s|#COREPRIORITY#|1000|g" \
        -e "s|#UNBLKCOREPRIORITY#|900|g" \
        -e "s|#UNBLKCORELDSOCONF#|usr/lib/fglrx-core/unblacklist_ld.so.conf|g" \
        -e "s|#CVERSION#|15.302|g" \
        -e "s|#SRCXARCH#|xpic_64a|g" \
        -e "s|#SRCARCH#|x86_64|g" \
        -e "s|#SRCOTHERARCH#|x86|g" \
        -e "s|#SRCLIBDIR#|lib64|g" \
        -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
        -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
        debian/$i.in > debian/$i;      \
done
sed: can't read debian/fglrx-amdcccle.dirs.in: No such file or directory
# remove exec bit on everything
find arch \
    etc \
    lib \
    module \
    usr \
    xpic_64a     -type f | xargs chmod -x
find: 'module': No such file or directory
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
   dh_update_autotools_config
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
cat debian/substvars >> debian/fglrx"".substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
# Code for the CORE package
dh_install -pfglrx""-core "arch/x86/usr/lib/*.so*"                 "usr/lib32"
dh_install -pfglrx""-core "arch/x86/usr/X11R6/lib/libatiadlxx.so"  "usr/lib32"
dh_install -pfglrx""-core "arch/x86/usr/lib/*.so*"                 "usr/lib32"
# Install the icd file for 32 bit OpenCL apps
dh_install -pfglrx""-core "arch/x86/etc/OpenCL/vendors/*.icd"      "etc/OpenCL/vendors"
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx""-core usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
dh_installdirs -pfglrx""-core
if [ -f "arch/x86_64/usr/X11R6/bin/amd-console-helper" ]; then \
    dh_install -pfglrx""-core "arch/x86_64/usr/X11R6/bin/amd-console-helper" usr/bin; \
    chmod ug+s debian/fglrx""-core/usr/bin/amd-console-helper; \
fi;
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
printf '# This file was installed by fglrx""\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.yDgXuf/debian/fglrx""-core/lib/fglrx/core-modprobe.conf
# This is empty, just for the alternative that blacklists the driver
echo "" > "/tmp/fglrx.yDgXuf/debian/fglrx""-core/usr/lib/fglrx-core/ld.so.conf"
# This is empty, just for the alternative that unblacklists the driver
echo "" > "/tmp/fglrx.yDgXuf/debian/fglrx""-core/usr/lib/fglrx-core/unblacklist_ld.so.conf"
dh_install -pfglrx""-core
# Make sure that every binary in bin is executable
find debian/fglrx""-core/usr/bin/ \
    -type f | xargs chmod a+x
# Make sure that every binary in sbin is executable
find debian/fglrx""-core/usr/sbin/ \
    -type f | xargs chmod a+x
# End of code for the CODE package
dh_install -pfglrx""    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx"" "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx"" "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
dh_installdirs -pfglrx""-dev
dh_installdocs -pfglrx"" usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx"" debian/AUTHORS
dh_installdocs -pfglrx"" debian/copyright
dh_installinit -pfglrx"" -n --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_install -pfglrx-amdcccle""
dh_install -pfglrx""
dh_install -pfglrx""-dev
# Create links for 32 bit libGL
dh_link -pfglrx"" usr/lib32/fglrx/libGL.so.1.2 usr/lib32/fglrx/libGL.so.1
dh_link -pfglrx""-dev usr/lib32/fglrx/libGL.so.1 usr/lib32/fglrx/libGL.so
dh_link -pfglrx""-dev usr/lib32/fglrx/libAMDXvBA.so.1 usr/lib32/fglrx/libAMDXvBA.so
dh_link -pfglrx""-dev usr/lib32/fglrx/libXvBAW.so.1 usr/lib32/fglrx/libXvBAW.so
# Make some additional scripts executable
find debian/fglrx-amdcccle""/usr/bin/ \
    -type f | xargs chmod a+x
# Make sure that every binary in bin is executable
find debian/fglrx""/usr/bin/ \
    -type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx""/ -name 'fglrx-libGL*'`; \
    do \
        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
        # Remove fglrx prefix \
        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
        full_path=`echo "$path$new_name"`; \
        mv -f $lib $full_path; \
done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx""/ -name 'fglrx-libglx*'`; \
    do \
        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
        new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
        # Remove fglrx prefix \
        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
        full_path=`echo "$new_path$new_name"`; \
        mv -f $lib $full_path; \
done
# Create links for PowerXpress X modules (except for extensions)
for i in \
    debian/fglrx""/usr/lib/fglrx/xorg/modules/* \
    ; do \
        orig_name=`echo $i  | sed -e "s|debian/fglrx""/||"`; \
        if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
            link_name=$orig_name ; \
            link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
            dh_link -pfglrx"" $orig_name $link_name ; \
        fi \
    done
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
#printf '# This file was installed by fglrx""\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.yDgXuf/debian/fglrx""/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/x86_64-linux-gnu/mesa" >        "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
#echo "/usr/lib/pxpress/lib" >>    "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/i386-linux-gnu/mesa" >>   "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
#echo "/usr/lib32/pxpress/lib" >>    "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative
echo "" > "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/fglrx/alt_ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.yDgXuf/debian/fglrx""/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
    lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx"" > \
    debian/fglrx"".modaliases
dh_modaliases
make: dh_modaliases: Command not found
debian/rules:268: recipe for target 'pre-binary-arch' failed
make: *** [pre-binary-arch] Error 127
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 296: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:15.302-0ubuntu1
dpkg-buildpackage: source distribution xenial
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.k9An8O
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
         control \
         dkms.conf \
         fglrx"".install \
         fglrx""-dev.install \
         fglrx""-dev.links \
         fglrx"".dirs \
         fglrx"".links \
         fglrx"".postinst \
         fglrx"".postrm \
         fglrx"".preinst \
         fglrx"".prerm \
         fglrx-amdcccle"".install \
         fglrx-amdcccle"".dirs \
         fglrx""-core.install \
         fglrx""-core.links \
         fglrx""-core.dirs \
         fglrx""-core.postinst \
         fglrx""-core.postrm \
         fglrx""-core.preinst \
         fglrx""-core.prerm \
         overrides/fglrx"" \
         overrides/fglrx""-dev \
         overrides/fglrx""-core \
         overrides/fglrx-amdcccle""; do \
    sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
        -e "s|#LIBDIR#|usr/lib|g" \
        -e "s|#LIBDIR32#|usr/lib32|g" \
        -e "s|#BINDIR#|usr/bin|g" \
        -e "s|#SBINDIR#|usr/sbin|g" \
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
        -e "s|#DRIVERNAME#|fglrx""|g" \
        -e "s|#MODULENAME#|fglrx|g" \
        -e "s|#DRIVERDIRNAME#|fglrx|g" \
        -e "s|#DRIVERDEVNAME#|fglrx""-dev|g" \
        -e "s|#DRIVERSRCNAME#|fglrx-installer|g" \
        -e "s|#DRIVERCORENAME#|fglrx""-core|g" \
        -e "s|#FLAVOUR#|""|g" \
        -e "s|#DRIVERCTRLNAME#|fglrx-amdcccle""|g" \
        -e "s|#INCLUDEDIR#|usr/include|g" \
        -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
        -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
        -e "s|#PXDIR#|usr/lib/pxpress|g" \
        -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
        -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
        -e "s|#PXDIRNAME#|pxpress|g" \
        -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
        -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
        -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
        -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
        -e "s|#COREDIRNAME#|fglrx-core|g" \
        -e "s|#COREDIR#|usr/lib/fglrx-core|g" \
        -e "s|#COREDIR32#|usr/lib32/fglrx-core|g" \
        -e "s|#CORELDSOCONF#|usr/lib/fglrx-core/ld.so.conf|g" \
        -e "s|#COREPRIORITY#|1000|g" \
        -e "s|#UNBLKCOREPRIORITY#|900|g" \
        -e "s|#UNBLKCORELDSOCONF#|usr/lib/fglrx-core/unblacklist_ld.so.conf|g" \
        -e "s|#CVERSION#|15.302|g" \
        -e "s|#SRCXARCH#|xpic_64a|g" \
        -e "s|#SRCARCH#|x86_64|g" \
        -e "s|#SRCOTHERARCH#|x86|g" \
        -e "s|#SRCLIBDIR#|lib64|g" \
        -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
        -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
        debian/$i.in > debian/$i;      \
done
sed: can't read debian/fglrx-amdcccle.dirs.in: No such file or directory
# remove exec bit on everything
find arch \
    etc \
    lib \
    module \
    usr \
    xpic_64a     -type f | xargs chmod -x
find: 'module': No such file or directory
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
   dh_update_autotools_config
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
cat debian/substvars >> debian/fglrx"".substvars
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
# Code for the CORE package
dh_install -pfglrx""-core "arch/x86/usr/lib/*.so*"                 "usr/lib32"
dh_install -pfglrx""-core "arch/x86/usr/X11R6/lib/libatiadlxx.so"  "usr/lib32"
dh_install -pfglrx""-core "arch/x86/usr/lib/*.so*"                 "usr/lib32"
# Install the icd file for 32 bit OpenCL apps
dh_install -pfglrx""-core "arch/x86/etc/OpenCL/vendors/*.icd"      "etc/OpenCL/vendors"
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx""-core usr/lib32/libatiuki.so.1.0 usr/lib32/libatiuki.so.1
dh_installdirs -pfglrx""-core
if [ -f "arch/x86_64/usr/X11R6/bin/amd-console-helper" ]; then \
    dh_install -pfglrx""-core "arch/x86_64/usr/X11R6/bin/amd-console-helper" usr/bin; \
    chmod ug+s debian/fglrx""-core/usr/bin/amd-console-helper; \
fi;
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
printf '# This file was installed by fglrx""\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.k9An8O/debian/fglrx""-core/lib/fglrx/core-modprobe.conf
# This is empty, just for the alternative that blacklists the driver
echo "" > "/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib/fglrx-core/ld.so.conf"
# This is empty, just for the alternative that unblacklists the driver
echo "" > "/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib/fglrx-core/unblacklist_ld.so.conf"
dh_install -pfglrx""-core
# Make sure that every binary in bin is executable
find debian/fglrx""-core/usr/bin/ \
    -type f | xargs chmod a+x
# Make sure that every binary in sbin is executable
find debian/fglrx""-core/usr/sbin/ \
    -type f | xargs chmod a+x
# End of code for the CODE package
dh_install -pfglrx""    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/*.*"           "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/fglrx/*.so*"     "usr/lib32/fglrx"
dh_installdirs -pfglrx"" "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx"" "arch/x86/usr/lib/*.so*"                 "usr/lib32/fglrx"
# Install the QT libraries
dh_install -pfglrx"" "arch/x86_64/usr/share/ati/lib64" "usr/share/ati"
dh_installdirs -pfglrx""-dev
dh_installdocs -pfglrx"" usr/share/doc/fglrx/* --exclude LICENSE.TXT
dh_installdocs -pfglrx"" debian/AUTHORS
dh_installdocs -pfglrx"" debian/copyright
dh_installinit -pfglrx"" -n --name="atieventsd" --no-start --update-rcd-params="defaults 31"
dh_install -pfglrx-amdcccle""
dh_install -pfglrx""
dh_install -pfglrx""-dev
# Create links for 32 bit libGL
dh_link -pfglrx"" usr/lib32/fglrx/libGL.so.1.2 usr/lib32/fglrx/libGL.so.1
dh_link -pfglrx""-dev usr/lib32/fglrx/libGL.so.1 usr/lib32/fglrx/libGL.so
dh_link -pfglrx""-dev usr/lib32/fglrx/libAMDXvBA.so.1 usr/lib32/fglrx/libAMDXvBA.so
dh_link -pfglrx""-dev usr/lib32/fglrx/libXvBAW.so.1 usr/lib32/fglrx/libXvBAW.so
# Make some additional scripts executable
find debian/fglrx-amdcccle""/usr/bin/ \
    -type f | xargs chmod a+x
# Make sure that every binary in bin is executable
find debian/fglrx""/usr/bin/ \
    -type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx""/ -name 'fglrx-libGL*'`; \
    do \
        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
        # Remove fglrx prefix \
        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
        full_path=`echo "$path$new_name"`; \
        mv -f $lib $full_path; \
done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx""/ -name 'fglrx-libglx*'`; \
    do \
        file_name=`echo $lib | awk -F/ '{print $NF}'`; \
        path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
        new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
        # Remove fglrx prefix \
        new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
        full_path=`echo "$new_path$new_name"`; \
        mv -f $lib $full_path; \
done
# Create links for PowerXpress X modules (except for extensions)
for i in \
    debian/fglrx""/usr/lib/fglrx/xorg/modules/* \
    ; do \
        orig_name=`echo $i  | sed -e "s|debian/fglrx""/||"`; \
        if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
            link_name=$orig_name ; \
            link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
            dh_link -pfglrx"" $orig_name $link_name ; \
        fi \
    done
# Blacklist any other driver that udev may want to load instead of fglrx
# and create an alias for the module so that it can be used as fglrx
#printf '# This file was installed by fglrx""\n# Do not edit this file manually\n\nblacklist radeon\nalias fglrx fglrx\nalias radeon off\nalias lbm-radeon off' > /tmp/fglrx.k9An8O/debian/fglrx""/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/x86_64-linux-gnu/mesa" >        "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
#echo "/usr/lib/pxpress/lib" >>    "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/i386-linux-gnu/mesa" >>   "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
#echo "/usr/lib32/pxpress/lib" >>    "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/pxpress/ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative
echo "" > "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx/alt_ld.so.conf"
# empty ld.so.conf for the fake multi-arch alternative for PXpress
echo "" > "/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/pxpress/alt_ld.so.conf"
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
    lib/modules/fglrx/build_mod/fglrxko_pci_ids.h fglrx fglrx"" > \
    debian/fglrx"".modaliases
dh_modaliases
rm debian/fglrx"".modaliases
# Remove all the binaries and shell scripts that already are in the
# core package from the x driver package
# PKG_driver_core always wins against PKG_driver
for i in $(find debian/fglrx""-core/ -exec file {} \; | grep -e "shell" -e "ELF" | cut -d: -f1); do \
    i_name="${i##*/}"; \
    for j in $(find debian/fglrx""/ -exec file {} \; | grep -e "shell" -e "ELF" | cut -d: -f1); do \
        j_name="${j##*/}"; \
        # Leave the DEBIAN directory and copyright files alone \
        if [ -z "`echo $i | grep -e \"DEBIAN\" -e \"copyright\"`" ] && [ "$i_name" = "$j_name" ]; then \
            echo "$i_name found in both fglrx""-core and fglrx"""; \
            #echo "orig: $i"; \
            #echo "dupe: $j"; \
            echo "removing duplicate in fglrx"": $j"; \
            rm -f "$j"; \
        fi; \
    done \
done
atigetsysteminfo.sh found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/sbin/atigetsysteminfo.sh
libaticalrt.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libaticalrt.so
libaticalcl.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libaticalcl.so
libaticaldd.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libaticaldd.so
libOpenCL.so.1 found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libOpenCL.so.1
libatiadlxx.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib/libatiadlxx.so
libatiadlxx.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libatiadlxx.so
libatiuki.so.1.0 found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libatiuki.so.1.0
atiodcli found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/bin/atiodcli
clinfo found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/bin/clinfo
libamdocl32.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libamdocl32.so
libamdocl12cl32.so found in both fglrx-core and fglrx
removing duplicate in fglrx: debian/fglrx/usr/lib32/fglrx/libamdocl12cl32.so
# Disable the stack markings on all binaries in PKG_driver_core
for i in $(find debian/fglrx""-core/ -exec file {} \; | grep -e "ELF" | cut -d: -f1); do \
    execstack -q $i && execstack -c $i || true; \
done
- debian/fglrx-core/usr/lib/libaticalrt.so
- debian/fglrx-core/usr/lib/libaticalcl.so
- debian/fglrx-core/usr/lib/libamdocl12cl64.so
- debian/fglrx-core/usr/lib/libaticaldd.so
- debian/fglrx-core/usr/lib/libOpenCL.so.1
- debian/fglrx-core/usr/lib/libamdocl64.so
- debian/fglrx-core/usr/lib/libatiadlxx.so
- debian/fglrx-core/usr/lib/libatiuki.so.1.0
- debian/fglrx-core/usr/bin/atiodcli
- debian/fglrx-core/usr/bin/amd-console-helper
- debian/fglrx-core/usr/bin/clinfo
execstack: "debian/fglrx-core/usr/src/fglrx-core-15.302/libfglrx_ip.a" is not a shared library
- debian/fglrx-core/usr/lib32/libaticalrt.so
- debian/fglrx-core/usr/lib32/libaticalcl.so
- debian/fglrx-core/usr/lib32/libaticaldd.so
- debian/fglrx-core/usr/lib32/libOpenCL.so.1
- debian/fglrx-core/usr/lib32/libatiadlxx.so
- debian/fglrx-core/usr/lib32/libamdocl32.so
- debian/fglrx-core/usr/lib32/libatiuki.so.1.0
- debian/fglrx-core/usr/lib32/libamdocl12cl32.so
# Disable the stack markings on all binaries in PKG_driver
for i in $(find debian/fglrx""/ -exec file {} \; | grep -e "ELF" | cut -d: -f1); do \
    execstack -q $i && execstack -c $i || true; \
done
- debian/fglrx/etc/ati/atiapfxx
- debian/fglrx/usr/sbin/amdnotifyui
- debian/fglrx/usr/sbin/atieventsd
- debian/fglrx/usr/lib/libfglrx_dm.so.1.0
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
- debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
- debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so
- debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so
- debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so
- debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
- debian/fglrx/usr/lib/libXvBAW.so.1.0
- debian/fglrx/usr/lib/dri/fglrx_dri.so
- debian/fglrx/usr/lib/libAMDXvBA.so.1.0
- debian/fglrx/usr/bin/aticonfig
- debian/fglrx/usr/bin/fgl_glxgears
- debian/fglrx/usr/bin/fglrxinfo
- debian/fglrx/usr/bin/atiode
- debian/fglrx/usr/share/ati/lib64/libQtCore.so.4
- debian/fglrx/usr/share/ati/lib64/libQtGui.so.4
- debian/fglrx/usr/lib32/fglrx/libfglrx_dm.so.1.0
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
- debian/fglrx/usr/lib32/fglrx/libXvBAW.so.1.0
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libAMDXvBA.so.1.0
- debian/fglrx/usr/lib32/libAMDXvBA.so.1.0
# Disable the stack markings on all binaries in PKG_control
for i in $(find debian/fglrx-amdcccle""/ -exec file {} \; | grep -e "ELF" | cut -d: -f1); do \
    execstack -q $i && execstack -c $i || true; \
done
- debian/fglrx-amdcccle/usr/bin/amdcccle
#Run the normal stuff
dh binary-arch
   dh_installdocs -a -Nfglrx -Nfglrx-dev
   dh_installchangelogs -a -Nfglrx -Nfglrx-dev
   dh_perl -a -Nfglrx -Nfglrx-dev
   dh_link -a -Nfglrx-core -Nfglrx -Nfglrx-dev
   dh_strip_nondeterminism -a
   dh_compress -a
   debian/rules override_dh_fixperms
make[1]: Entering directory '/tmp/fglrx.k9An8O'
dh_fixperms -Xamd-console-helper
make[1]: Leaving directory '/tmp/fglrx.k9An8O'
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx-core/usr/lib/fglrx-core/ld.so.conf: File truncated
objdump: debian/fglrx-core/usr/lib/fglrx-core/unblacklist_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory '/tmp/fglrx.k9An8O'
dh_shlibdeps -l/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx:/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx/bin:/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib/fglrx/sbin:/tmp/fglrx.k9An8O/debian/fglrx""/usr/lib32/fglrx:/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib/fglrx:/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib/fglrx/bin:/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib/fglrx/sbin:/tmp/fglrx.k9An8O/debian/fglrx""-core/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin
dpkg-shlibdeps: error: couldn't find library libQtCore.so.4 needed by debian/fglrx/usr/share/ati/lib64/libQtGui.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol _XReadPad: it's probably a plugin
dpkg-shlibdeps: warning: 33 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol _XReply used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol _XFlush used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol _XRead used by debian/fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XFreeGC used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XDisplayString used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XTranslateCoordinates used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol dlopen used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol sem_post used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol _Znam used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol sem_close used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XPutImage used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol pthread_mutexattr_init used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/fglrx/usr/lib/libAMDXvBA.so.1.0 found in none of the libraries
dpkg-shlibdeps: warning: 29 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/fglrx/usr/sbin/amdnotifyui was not linked against libXfixes.so.3 (it uses none of the library's symbols)
dpkg-shlibdeps: error: cannot continue due to the error above
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to use -l.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars -l/tmp/fglrx.k9An8O/debian/fglrx/usr/lib/fglrx -l/tmp/fglrx.k9An8O/debian/fglrx/usr/lib/fglrx/bin -l/tmp/fglrx.k9An8O/debian/fglrx/usr/lib/fglrx/sbin -l/tmp/fglrx.k9An8O/debian/fglrx/usr/lib32/fglrx -l/tmp/fglrx.k9An8O/debian/fglrx-core/usr/lib/fglrx -l/tmp/fglrx.k9An8O/debian/fglrx-core/usr/lib/fglrx/bin -l/tmp/fglrx.k9An8O/debian/fglrx-core/usr/lib/fglrx/sbin -l/tmp/fglrx.k9An8O/debian/fglrx-core/usr/lib32/fglrx debian/fglrx/usr/sbin/amdnotifyui debian/fglrx/usr/sbin/atieventsd debian/fglrx/usr/lib/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/libXvBAW.so.1.0 debian/fglrx/usr/lib/dri/fglrx_dri.so debian/fglrx/usr/lib/libAMDXvBA.so.1.0 debian/fglrx/usr/bin/aticonfig debian/fglrx/usr/bin/fgl_glxgears debian/fglrx/usr/bin/fglrxinfo debian/fglrx/usr/bin/atiode debian/fglrx/usr/share/ati/lib64/libQtCore.so.4 debian/fglrx/usr/share/ati/lib64/libQtGui.so.4 returned exit code 2
debian/rules:470: recipe for target 'override_dh_shlibdeps' failed
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory '/tmp/fglrx.k9An8O'
debian/rules:458: recipe for target 'binary-arch' failed
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/xenial
geek@geek-ThinkPad-T400:/usr/share/ati$ 

```

Can anyone shed light on this error? I don't know how to approach this.

---

### Post by X-RED_Tech on 2016-03-01
Legacy hardware are no longer supported by AMD.
You have to keep the open source Radeon.

---

### Post by Bucky Ball on 2016-03-01
*Thread moved to **Ubuntu Development Version**.*

Xenial is not released until April 2016, so not a good place to start. Expect the unexpected.

If you are new to this I strongly advise you to start with a supported release, the very stable 14.04 LTS would be a good choice or 15.10 and then upgrade it to 16.04 LTS in April. LTS releases have five years support, the interim releases (everything else) has nine months.

Good luck.

---

### Post by Bashing-om on 2016-03-01
glenn_morrissey2; Yeah;

> **X-RED_Tech said:**
> Legacy hardware are no longer supported by AMD.
You have to keep the open source Radeon.

concur as you are running:
> 
[Mobility Radeon HD 3450/3470]

IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 (+) uses X-server v1.13 (+).
That's because, starting with Ubuntu [color=red]12.04.2[/color], the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.

Hint: 12.04.[color=green]1[/color] has support 'til April 2019 for the FGLRX driver

[INDENT][INDENT]there is more to say
[INDENT][INDENT]but this says a bunch
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by monkeyman_stones on 2016-07-30
Download the latest Linux Install package for the AMD driver for your Video card (the one which is not listed as specific to Ubuntu). It appears you did so as you seem to have the same package I do and attempted to install.
Unizip the downloaded package from within it's folder.
Install the required dependencies (and if you already have them then make certain they are up to date):
"sudo apt-get install devscripts"
"sync"
"sudo sync"
"sudo reboot" (devscripts requires a reboot in order to function)
(Upon restart):
"sudo apt-get install dkms dh-modaliases execstack"
"sync"
"sudo sync"
Change Directory to the folder the driver was downloaded to was downloaed to "cd /home/"my name"/Downloads/" (This is where my download was saved to but change you cd command to wherever yours was downloaded to) or whatever other path you've chosen to download it to.
Give it the correct privileges:  "chmod +x amd-driver-installer-15.302-x86.x86_64.run"
Now, start the installer:  "sudo ./amd-driver-installer-15.302-x86.x86_64.run"
This will attempt to install your Radeon video driver as well as it's extra components (such as the settings program for it).  If you experience an error it will tell you which dependency is missing (but in 16.04 64-bit only the applications I listed are currently required as best I can tell. With the problem you listed it appears you do not have the devscripts dependency installed).
I will come back and delete this post if it does not work after I reboot (as I only just finished installing it on my system).

I hope this helps,
David

---

### Post by monkeyman_stones on 2016-07-30
So the installation worked [IMG]https://www.dropbox.com/s/5pru82mbsc6ngwh/After%20AMD%20ATI%20Driver%20install.png?dl=0[/IMG], but it is unable to detect my Radeon card either because of it's type or because Ubuntu may have blocked it's use in 16.04 [IMG]https://www.dropbox.com/s/wnqg676lcx7umjo/AMD%20ATI%20install%20blocked%20by%20Ubuntu%20or%20due%20to%20my%20specific%20Video%20card.png?dl=0[/IMG].

---

### Post by Bashing-om on 2016-07-30
monkeyman_stones; Yuk.

Be aware there is NO FGLRX support in xenial .
See the release notes:
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
[http://ubuntuforums.org/showthread.php?t=2317751](http://ubuntuforums.org/showthread.php?t=2317751)

AMD is providing all their efforts in support of the open source driver for 16.04.

[INDENT][INDENT]things are going to look up
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2016-07-30
*Thread moved from **Ubuntu Development Release** to **Hardware**.*

... as during its sleep 16.04 has been released and 16.10 is now the development release.

---

