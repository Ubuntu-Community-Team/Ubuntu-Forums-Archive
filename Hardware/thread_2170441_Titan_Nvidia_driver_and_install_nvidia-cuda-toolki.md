---
title: "Titan Nvidia driver and install nvidia-cuda-toolkit for blender"
date: 2013-08-26
forum: Hardware
---

### Post by Damien_MONTEILLARD on 2013-08-26
Hi

I have a new computer for special blender cycles 2.68a with nvidia cards Titan.
I installed ubuntu 13.04 with no problem.
Graphics drivers recommended and tested for ubuntu is 313.
To use blender cycles 2.68a so I need to install nvidia-cuda-toolkit Version 5 except when installing it asks me to install the 304 driver.
This driver is not compatible with my card because it is too old.

What should I do to properly install nvidia-cuda-toolkit with the correct driver or the 313?

---

### Post by Damien_MONTEILLARD on 2013-08-27
I have installed 313 recommended driver for my titan cards and it work on my station.
So i will start another time $ sudo apt-get install nvidia-cuda-toolkit
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  linux-image-generic
Veuillez utiliser « apt-get autoremove » pour le supprimer.
Les paquets supplémentaires suivants seront installés : 
  ca-certificates-java cpp-4.6 default-jre default-jre-headless g++-4.6
  gcc-4.6 gcc-4.6-base icedtea-7-jre-jamvm java-common libatk-wrapper-java
  libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libcublas5.0
  libcudart5.0 libcufft5.0 libcuinj64-5.0 libcurand5.0 libcusparse5.0
  libdrm-dev libgconf2-4 libgif4 libgl1-mesa-dev libgnome2-0 libgnome2-bin
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libidl-common libidl0
  libkms1 libnpp5.0 libnss3-1d libnvtoolsext5.0 liborbit2 libpthread-stubs0
  libpthread-stubs0-dev libstdc++6-4.6-dev libthrust-dev libvdpau-dev
  libvdpau1 libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev
  libxcb-glx0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxxf86vm-dev mesa-common-dev nvidia-cuda-dev nvidia-cuda-doc
  nvidia-cuda-gdb nvidia-opencl-dev nvidia-profiler nvidia-visual-profiler
  opencl-headers openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib
  ttf-dejavu-extra tzdata-java x11proto-core-dev x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev
  x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev
  xorg-sgml-doctools xtrans-dev
Paquets suggérés :
  gcc-4.6-locales g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  gcc-4.6-multilib libmudflap0-4.6-dev libgcc1-dbg libgomp1-dbg
  libquadmath0-dbg libmudflap0-dbg binutils-gold equivs libbonobo2-bin
  desktop-base libgnomevfs2-bin libgnomevfs2-extra gamin fam gnome-mime-data
  libstdc++6-4.6-doc libvdpau-doc nvidia-vdpau-driver vdpau-driver libxcb-doc
  libxext-doc libcupti-dev icedtea-7-plugin sun-java6-fonts
  fonts-ipafont-gothic fonts-ipafont-mincho ttf-telugu-fonts ttf-oriya-fonts
  ttf-kannada-fonts ttf-bengali-fonts
Les NOUVEAUX paquets suivants seront installés :
  ca-certificates-java cpp-4.6 default-jre default-jre-headless g++-4.6
  gcc-4.6 gcc-4.6-base icedtea-7-jre-jamvm java-common libatk-wrapper-java
  libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libcublas5.0
  libcudart5.0 libcufft5.0 libcuinj64-5.0 libcurand5.0 libcusparse5.0
  libdrm-dev libgconf2-4 libgif4 libgl1-mesa-dev libgnome2-0 libgnome2-bin
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libidl-common libidl0
  libkms1 libnpp5.0 libnss3-1d libnvtoolsext5.0 liborbit2 libpthread-stubs0
  libpthread-stubs0-dev libstdc++6-4.6-dev libthrust-dev libvdpau-dev
  libvdpau1 libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev
  libxcb-glx0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxxf86vm-dev mesa-common-dev nvidia-cuda-dev nvidia-cuda-doc
  nvidia-cuda-gdb nvidia-cuda-toolkit nvidia-opencl-dev nvidia-profiler
  nvidia-visual-profiler opencl-headers openjdk-7-jre openjdk-7-jre-headless
  openjdk-7-jre-lib ttf-dejavu-extra tzdata-java x11proto-core-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev

And it don't remove 313 driver. So good.
So i think i can install nvidia-cuda-toolkit properly. Is it ?

---

### Post by Damien_MONTEILLARD on 2013-08-28
I have installed nvidia-cuda-toolkit package of ubntu 13.04 and blender is working.
bye

---

