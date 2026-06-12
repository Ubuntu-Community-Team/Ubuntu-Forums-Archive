---
title: "Transmission 1.70 update problem (8.04)"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Hakker on 2009-06-14
when I try to update transmission from Getdeb to 1.7 i get the following error during the transmission-common package update.

(reading database ... 183170 files and directories currently installed.)
Preparing to replace transmission-common 1.06-0ubuntu6 (using .../transmission-common_1.70-1~getdeb1_all.deb) ...
unpacking replacement transmission-common ...
dpkg: error processing /home/hakker/Desktop/transmission-common_1.70-1~getdeb1_all.deb (--install):
 trying to overwrite `/usr/share/transmission/web/javascript/transmission.js', which is also in package transmission-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)

it won't even try to update the transmission-gtk package asit says it misses dependencies.

And yes I do want it updated as it still uses 1.34 or so because the package itself never got updated on the update manager so getdeb is basically a need for updates and i figured this is an Ubuntu issue in general.
I hope I placed it in the correct forum.

---

### Post by zvacet on 2009-06-15
Whitch dependencies are missing?You should have them all but just in case check if you have installed **build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-dev**.

---

