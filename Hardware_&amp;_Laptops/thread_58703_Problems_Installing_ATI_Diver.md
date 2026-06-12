---
title: "Problems Installing ATI Diver"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by RogerSilva on 2005-08-21
Hi,
I'm new user of Ubuntu(I'm using verison 5.04 for AMD64).
I hava an ATI Radeon X600XT video card and I'm trying to install
ATI Proprietary Linux x86_64 Driver Version 8.16.20.
Then after running the installer, I tryed to generate the package for Ubuntu 5.04, but it fails with the folowing erros:
> 
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.16.20-1
dpkg-buildpackage: source maintainer is ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture is amd64
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
 fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
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
	usr/X11R6 \
	usr/X11R6/bin \
	usr/X11R6/lib \
	usr/X11R6/lib/modules \
	usr/share/fglrx/diversions
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
	usr/X11R6/lib32 \
	usr/X11R6/lib32/modules \
	emul/ia32-linux/usr/X11R6/lib \
	emul/ia32-linux/usr/X11R6/lib/modules/driver \
	emul/ia32-linux/usr/X11R6/lib/modules/linux \
	emul/ia32-linux/usr/X11R6/lib/modules/dri
dh_installdirs -pxorg-driver-fglrx-dev \
	usr/X11R6 \
	usr/X11R6/include \
	usr/X11R6/lib \
	usr/include
dh_installdirs -pfglrx-kernel-source \
	usr/src/modules/fglrx \
	usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
	usr/X11R6 \
	usr/X11R6/bin \
	usr/share \
	usr/share/applnk \
	usr/share/gnome \
	usr/share/gnome/apps \
	usr/share/icons \
	usr/share/pixmaps
dh_installdirs -pfglrx-sources \
	usr/src
dh_install
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/X11R6/bin"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"     "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*" "usr/X11R6/lib/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"       "usr/X11R6/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*"   "usr/X11R6/lib32/modules"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/libGL.so.1.2" \
	"emul/ia32-linux/usr/X11R6/lib/libGL.so.1.2"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/libfglrx_gamma.so.1.0" \
	"emul/ia32-linux/usr/X11R6/lib/libfglrx_gamma.so.1.0"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/driver/fglrx_drv.o" \
	"emul/ia32-linux/usr/X11R6/lib/modules/driver/fglrx_drv.o"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/linux/libfglrxdrm.a" \
	"emul/ia32-linux/usr/X11R6/lib/modules/linux/libfglrxdrm.a"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/atiogl_a_dri.so" \
	"emul/ia32-linux/usr/X11R6/lib/modules/dri/atiogl_a_dri.so"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/fglrx_dri.so" \
	"emul/ia32-linux/usr/X11R6/lib/modules/dri/fglrx_dri.so"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/X11R6/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
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
	usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
 && chown -R root:src modules \
 && tar -c modules | bzip2 > fglrx.tar.bz2 \
 && rm -rf modules)
# install panel files
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/X11R6/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pixmaps"
dh_install -A -pfglrx-control "usr/share/gnome/apps/fireglcontrol.desktop"      "usr/share/gnome/apps"
dh_install -A -pfglrx-control "usr/share/applnk/fireglcontrol.kdelnk" "usr/share/applnk"
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so: error while loading shared libraries: libfakeroot.so.0: cannot open shared object file: No such file or directory
dpkg-shlibdeps: failure: ldd on `debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so' gave error exit status 1
dh_shlibdeps: command returned error code 256
make: ** [binary] Erro 1
~/linuxDrivers/ATI/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/5.04
 

Please, could anyone help??

Thanks a lot,
Roger Silva

---

### Post by RogerSilva on 2005-08-21
does anyone knows how to fix this problem??
I am new in Linux and I don't have any Ideias on how to fix it...

thanks,
roger

---

### Post by johannes on 2005-08-23
I haven't had any luck installing the 8.16.20 drivers on my computer, but I use a different card so perhaps I can help you anyways with something.

Have you installed the packages "build-essential" and "linux-headers-2.6.10-5" and "linux-headers-2.6.10-5-k7"? If not, do so. Try installing again and post the results here.

---

### Post by RogerSilva on 2005-08-23
[QUOTE=johannes]I haven't had any luck installing the 8.16.20 drivers on my computer, but I use a different card so perhaps I can help you anyways with something.

Have you installed the packages "build-essential" and "linux-headers-2.6.10-5" and "linux-headers-2.6.10-5-k7"? If not, do so. Try installing again and post the results here.[/QUOTE]
Hi, thanks for helping....
Before I've tried to install the dirvers, I had installed all the kernel source and headers...
I have no idea waht is causing this error...

thanks,
Roger

---

### Post by johannes on 2005-08-23
I don't know if it will help, but as it seems it has problems with the libfglrx_gamma.1, try installing "xorg-driver-fglrx-dev". Also, install "fakeroot". If it doesn't help, you can remove them.

---

### Post by RogerSilva on 2005-08-23
[QUOTE=johannes]I don't know if it will help, but as it seems it has problems with the libfglrx_gamma.1, try installing "xorg-driver-fglrx-dev". Also, install "fakeroot". If it doesn't help, you can remove them.[/QUOTE]
hi,
thanks again for helping.
I installed the fakeroot, the kernel source and headers packages before trying to install the ATI driver...
Where can I find this "xorg-driver-fglrx-dev"?
The problem is that this ATI driver version is the only driver that supports my video card(previously versions doesn't support it)...

thanks,
Roger

---

### Post by fragmental on 2005-08-23
[QUOTE=RogerSilva]hi,
thanks again for helping.
I installed the fakeroot, the kernel source and headers packages before trying to install the ATI driver...
Where can I find this "xorg-driver-fglrx-dev"?
The problem is that this ATI driver version is the only driver that supports my video card(previously versions doesn't support it)...

thanks,
Roger[/QUOTE]
 > debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so: error while loading shared libraries: libfakeroot.so.0: cannot open shared object file: No such file or directory

Make sure you have the a library called "libfakeroot.so.0".  Sometimes installed libraries have different names so you might have to create a symbolic link by using "ln -s" from whatever your libfakeroot library is called.  Also, you could have the wrong fakeroot installed.  Make sure there are not any alternate fakeroot packages in synaptic that you might need.  For example if one of them is for x86 and one is for amd64 or one is a different version than the other.  A lot of the time, all you need is a symbolic link though.

---

### Post by johannes on 2005-08-23
[QUOTE=RogerSilva]
Where can I find this "xorg-driver-fglrx-dev"?[/QUOTE]
You should be able to apt-get "xorg-driver-fglrx-dev" if you have enabled the [extra repositories](http://ubuntuguide.org/#extrarepositories).

---

### Post by fragmental on 2005-08-23
[QUOTE=johannes]You should be able to apt-get "xorg-driver-fglrx-dev" if you have enabled the [extra repositories](http://ubuntuguide.org/#extrarepositories).[/QUOTE]

I dont't think you  need that package, because it's the old 8.8 stuff and you didn't really need it for the 8.8 stuff either.

---

### Post by SWAT on 2005-08-24
Why did you try to create your own package? Just select the "install driver" and it will directly install the drivers. So there is actually no need to create the package first. I've got my ATI drivers working here fine. Just use the ATI installer installer on the website (it's 54MB or something), then just follow the instructions.

On another note, it's quite possible that the 64-bit version gives you trouble. That's why I installed the 32-bit version of Ubuntu, because there aren't enough applications that are compiled/created for 64-bit yet.

---

### Post by RogerSilva on 2005-08-24
[QUOTE=SWAT]Why did you try to create your own package? Just select the "install driver" and it will directly install the drivers. So there is actually no need to create the package first. I've got my ATI drivers working here fine. Just use the ATI installer installer on the website (it's 54MB or something), then just follow the instructions.

On another note, it's quite possible that the 64-bit version gives you trouble. That's why I installed the 32-bit version of Ubuntu, because there aren't enough applications that are compiled/created for 64-bit yet.[/QUOTE]

Hi, 
I am trying to install the 64 bits ATI driver...
The autommatic install simply corrupt a lot of OpenGl libraries(I had to install all libraries modified by the installer again in order to X-Server works) and the fglrx kernel module display weird messages about memory allocation...

thanks,
Roger

---

### Post by fragmental on 2005-08-24
[QUOTE=RogerSilva]Hi, 
I am trying to install the 64 bits ATI driver...
The autommatic install simply corrupt a lot of OpenGl libraries(I had to install all libraries modified by the installer again in order to X-Server works) and the fglrx kernel module display weird messages about memory allocation...

thanks,
Roger[/QUOTE]
 Have you checked and searched the rage3d forum? [http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88)  If you post a question there, you might get better answers.

---

### Post by graigsmith on 2005-08-24
[QUOTE=SWAT]Why did you try to create your own package? Just select the "install driver" and it will directly install the drivers. So there is actually no need to create the package first. I've got my ATI drivers working here fine. Just use the ATI installer installer on the website (it's 54MB or something), then just follow the instructions.

On another note, it's quite possible that the 64-bit version gives you trouble. That's why I installed the 32-bit version of Ubuntu, because there aren't enough applications that are compiled/created for 64-bit yet.[/QUOTE]
 if you do install it from the installer, ati does include an uninstaller.  i forget where it is and what the name is.  but if you search for ati, you should be able to find the uninstall along with some other ati things in a folder.

---

