---
title: "envy nvidia error"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by amer1337 on 2007-10-11
trying to install the nvidia driver and it gives me this

python pulse.py nvidia 
root@plutonium:/usr/share/envy# python pulse.py nvidia
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce Go 6100
Your graphic card is supported by the latest driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1.0-dev libaudio-dev libbeecrypt6 libcairo2-dev libcupsys2-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev
  libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev
  libgpg-error-dev libice-dev libjpeg62-dev liblcms1-dev liblzo-dev libmng-dev
  libopencdk8-dev libpango1.0-dev libpng12-dev libpopt-dev libqt3-headers
  librpm4 libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcursor-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxmu-dev
  libxmu-headers libxrandr-dev libxrender-dev libxt-dev mesa-common-dev
  qt3-dev-tools x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xf86misc-dev x11proto-xf86vidmode-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgcrypt11-doc libglib2.0-doc gnutls-doc gnutls-bin
  libgtk2.0-doc libpango1.0-doc imagemagick libqt3-i18n qt3-doc alien mailx
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  kernel-wedge libatk1.0-dev libaudio-dev libbeecrypt6 libcairo2-dev
  libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libgnutls-dev libgpg-error-dev libgtk2.0-dev libice-dev libjpeg62-dev
  liblcms1-dev liblzo-dev libmng-dev libopencdk8-dev libpango1.0-dev
  libpng12-dev libpopt-dev libqt3-headers libqt3-mt-dev librpm4 libsm-dev
  libtasn1-3-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers
  libxrandr-dev libxrender-dev libxt-dev libxtst-dev libxxf86misc-dev
  libxxf86vm-dev mesa-common-dev qt3-dev-tools rpm sharutils x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
0 upgraded, 64 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.2MB of archives.
After unpacking 70.7MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  x11proto-core-dev libice-dev libsm-dev libxau-dev libxdmcp-dev
  x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-render-dev
  libxrender-dev x11proto-xext-dev x11proto-fixes-dev libxfixes-dev
  libxcursor-dev libxext-dev libexpat1-dev zlib1g-dev libfreetype6-dev
  libfontconfig1-dev libxft-dev libxi-dev x11proto-xinerama-dev
  libxinerama-dev libxmu-headers x11proto-randr-dev libxrandr-dev libxt-dev
  x11proto-record-dev libxtst-dev x11proto-xf86misc-dev libxxf86misc-dev
  x11proto-xf86vidmode-dev libxxf86vm-dev kernel-wedge libglib2.0-dev
  libatk1.0-dev libbeecrypt6 libpng12-dev libcairo2-dev libgpg-error-dev
  libgcrypt11-dev libtasn1-3-dev libpopt-dev libopencdk8-dev liblzo-dev
  libgnutls-dev libcupsys2-dev mesa-common-dev libgl1-mesa-dev
  libglu1-mesa-dev libpango1.0-dev libgtk2.0-dev libjpeg62-dev liblcms1-dev
  libmng-dev libqt3-headers libxmu-dev libaudio-dev qt3-dev-tools
  libqt3-mt-dev librpm4 rpm sharutils
E: There are problems and -y was used without --force-yes
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

---

### Post by renzokuken on 2007-10-12
you should use the restricted drivers manager instead to install nvidia drivers......envy is not supported

---

