---
title: "Intel Graphics Driver Installer broke my touchpad"
date: 2013-03-10
forum: Hardware
---

### Post by Inoki on 2013-03-10
Hi guys,

I installed the **[Intel Graphics Driver Installer]("http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html")** and upgraded my drivers through it but encountered a serious issue. After the update my touchpad doesn't work properly. The buttons work with a 5 sec delay and movement doesn't work at all.

Any idea how to fix this?

---

### Post by Inoki on 2013-03-10
[COLOR=#ff0000][SIZE=5][B]*** Warning!!! *** DO NOT INSTALL THIS. It broke my entire Ubuntu installation. First it broke my touchpad and then the whole Steam installation, since it removed vital Mesa components.

[/B][/SIZE][/COLOR]When attempting to re-install Steam I got the following errors when pulling resources:

> dpkg: chyba pri spracovávaní /var/cache/apt/archives/libgl1-mesa-glx_9.0.1-0ubuntu1~precise7.3_i386.deb (--unpack):
 './usr/share/doc/libgl1-mesa-glx/changelog.Debian.gz' is different from the same file on the system
dpkg-deb (podproces): podproces dáta ukon&#269;ený signálom (Preru&#353;ená rúra)
dpkg-deb: chyba: podproces <dekompresia> vrátil chybový kód 2
Vyskytli sa chyby po&#269;as spracovania:
 /var/cache/apt/archives/libgl1-mesa-dri_9.0.1-0ubuntu1~precise7.3_i386.deb
 /var/cache/apt/archives/libglapi-mesa_9.0.1-0ubuntu1~precise7.3_i386.deb
 /var/cache/apt/archives/libgl1-mesa-glx_9.0.1-0ubuntu1~precise7.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by whitlockau on 2013-04-19
I had to reinstall the xserver-xorg-input-synaptics package (and restart X) to get the touchpad working again.  (I did this after removing the intel driver via the instructions at [http://theclonker.de/?p=89](http://theclonker.de/?p=89), so I don't know if that would work with the intel driver still installed.)

---

