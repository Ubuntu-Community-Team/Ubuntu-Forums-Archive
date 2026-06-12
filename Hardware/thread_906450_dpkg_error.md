---
title: "dpkg error"
date: 2008-08-31
forum: Hardware
---

### Post by fredunderhill on 2008-08-31
i recently downloaded this icon theme: [http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562) from gnome look.com. in order to install the extra icons, i had to merge the usr folder with the one in my root directory. now, whenever i try to install/uninstall programs, via terminal or add/remove programs or in the update manager, i get a message like this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev libgnutlsxx13 libtasn1-3-dev libatk1.0-dev libaudiofile-dev
  libgpg-error-dev libgda3-common python-gnome2-extras libpango1.0-dev
  libgcrypt11-dev libxi-dev libgdl-gnome-1-0 libgnome-keyring-dev
  libavahi-client-dev python-utidylib libtidy-0.99-0 libbonobo2-dev
  libgnutls-dev python-ctypes libjpeg62-dev python-feedparser libart-2.0-dev
  libesd0-dev libgnomevfs2-dev liblzo2-dev libgda3-bin libgda3-3
  libselinux1-dev libxft-dev libgnome2-dev libavahi-glib-dev
  libavahi-common-dev python-chardet libsepol1-dev libgdl-1-0 libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  4digits
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
10 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory





i think i need a new usr file. but who knows, i'm a total noob on ubuntu. running hardy on a dell latitude d600. please help.

---

