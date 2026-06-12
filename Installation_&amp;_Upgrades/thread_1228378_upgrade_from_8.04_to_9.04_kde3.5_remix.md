---
title: "upgrade from 8.04 to 9.04 kde3.5 remix"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by katoiam on 2009-07-31
I have just upgraded to 9.04 from 8.04, im still not set on kde4 though 4.3 is looking a lot better (though uses too many resources for my old laptop!!) so I have been waiting to upgrade after redaing about the remix I though it was the best of both world. So I went for it, how ever after under going the whole experience I have kde4 fine but when installing kde3.5 I get this :
Errors were encountered while processing:
 kdebase-kde3
 kde-guidance-powermanager-kde3
 kde-guidance-kde3
 kdebase-runtime-data-common-kde3
 ksmserver-kde3
 konqueror-kde3
 konq-plugins-kde3
 konqueror-nsplugins-kde3
 kmplayer-konq-plugins-kde3
Ive tried running aptitude Ive tried sudo apt-get -f install, Ive even tried  sudo dpkg --configure -a and nothing works!!!! Iam in kde3.5 now but it looks really old I only have plastic window decoration!
It all feels a bit like I have gone back in time a bit!
can any one help me work out how to finish the install and why my kde3 seems to have gone back in time
thanks
ciao 
kate and liam

---

### Post by Partyboi2 on 2009-07-31
Hi, can you open a terminal and post the output for
```
sudo dpkg --configure -a 
```

---

### Post by katoiam on 2009-08-01
dpkg: dependency problems prevent configuration of kdebase-kde3:
 kdebase-kde3 depends on kfind-kde3 (>= 4:3.5.10-0ubuntu4~intrepid17); however:
  Package kfind-kde3 is not installed.
dpkg: error processing kdebase-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-guidance-powermanager-kde3:
 kde-guidance-powermanager-kde3 depends on python-kde3-kde3; however:
  Package python-kde3-kde3 is not installed.
dpkg: error processing kde-guidance-powermanager-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-guidance-kde3:
 kde-guidance-kde3 depends on python-kde3-kde3; however:
  Package python-kde3-kde3 is not installed.
dpkg: error processing kde-guidance-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime-data-common-kde3:
 kdebase-runtime-data-common-kde3 depends on kdebase-kde3; however:
  Package kdebase-kde3 is not configured yet.
dpkg: error processing kdebase-runtime-data-common-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksmserver-kde3:
 ksmserver-kde3 depends on kdebase-runtime-data-common-kde3; however:
  Package kdebase-runtime-data-common-kde3 is not configured yet.
dpkg: error processing ksmserver-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror-kde3:
 konqueror-kde3 depends on kfind-kde3 (= 4:3.5.10-0ubuntu4~intrepid17); however:
  Package kfind-kde3 is not installed.
dpkg: error processing konqueror-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konq-plugins-kde3:
 konq-plugins-kde3 depends on konqueror-kde3 (>= 4:3.5.8-1); however:
  Package konqueror-kde3 is not configured yet.
dpkg: error processing konq-plugins-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konqueror-nsplugins-kde3:
 konqueror-nsplugins-kde3 depends on konqueror-kde3; however:
  Package konqueror-kde3 is not configured yet.
dpkg: error processing konqueror-nsplugins-kde3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins-kde3:
 kmplayer-konq-plugins-kde3 depends on konqueror-kde3; however:
  Package konqueror-kde3 is not configured yet.
dpkg: error processing kmplayer-konq-plugins-kde3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdebase-kde3
 kde-guidance-powermanager-kde3
 kde-guidance-kde3
 kdebase-runtime-data-common-kde3
 ksmserver-kde3
 konqueror-kde3
 konq-plugins-kde3
 konqueror-nsplugins-kde3
 kmplayer-konq-plugins-kde3

---

### Post by katoiam on 2009-08-01
I have also just tried this to no avail:
katoiam@ubuntu:~$ sudo aptitude install --with-recommends kubuntu-desktop-kde3
[sudo] password for katoiam:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  kde-guidance-kde3 kde-guidance-powermanager-kde3 kipi-plugins-kde3
The following NEW packages will be installed:
  desktop-effects-kde-kde3 kaffeine-kde3 kfind-kde3 kmix-kde3
  kubuntu-desktop-kde3 network-manager-kde-kde3
The following packages will be REMOVED:
  avant-window-navigator-data-trunk{u} k3b-data{u} libcapseo0{u}
  libcaptury0{u} libevent1{u} libk3b3{u} libk3b3-extracodecs{u}
  libwebkit-1.0-1{u} socat{u} tsocks{u}
The following partially installed packages will be configured:
  kdebase-kde3 kdebase-runtime-data-common-kde3 kmplayer-konq-plugins-kde3
  konq-plugins-kde3 konqueror-kde3 konqueror-nsplugins-kde3 ksmserver-kde3
0 packages upgraded, 7 newly installed, 10 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 3568kB will be used.
The following packages have unmet dependencies:
  kde-guidance-kde3: Depends: python-kde3-kde3 but it is not installable
  kde-guidance-powermanager-kde3: Depends: python-kde3-kde3 but it is not installable
  kipi-plugins-kde3: Depends: libgpod3-nogtk (>= 0.6.0) but it is not installable or
                              libgpod3 (>= 0.6.0) but it is not installable
E: I wasn't able to locate file for the ark package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Install the following packages:
python-kde3-kde3 [3.16.2-0ubuntu1 (jaunty)]

Keep the following packages at their current version:
kipi-plugins-kde3 [Not Installed]

Leave the following dependencies unresolved:
kaffeine-kde3 recommends gdebi-kde-kde3
kubuntu-desktop-kde3 recommends kdebluetooth-kde3
kubuntu-desktop-kde3 recommends kipi-plugins-kde3
kubuntu-desktop-kde3 recommends kubuntu-docs-kde3
kubuntu-desktop-kde3 recommends strigi-applet
kubuntu-desktop-kde3 recommends system-config-printer-kde-kde3
Score is -1090

Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  desktop-effects-kde-kde3 kaffeine-kde3 kfind-kde3 kmix-kde3
  kubuntu-desktop-kde3 network-manager-kde-kde3 python-kde3-kde3{a}
The following packages will be REMOVED:
  avant-window-navigator-data-trunk{u} k3b-data{u} libcapseo0{u}
  libcaptury0{u} libevent1{u} libk3b3{u} libk3b3-extracodecs{u}
  libwebkit-1.0-1{u} socat{u} tsocks{u}
The following partially installed packages will be configured:
  kde-guidance-kde3 kde-guidance-powermanager-kde3 kdebase-kde3
  kdebase-runtime-data-common-kde3 kmplayer-konq-plugins-kde3
  konq-plugins-kde3 konqueror-kde3 konqueror-nsplugins-kde3 ksmserver-kde3
The following packages are RECOMMENDED but will NOT be installed:
  kipi-plugins-kde3
0 packages upgraded, 7 newly installed, 10 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 45.1MB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the ark package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the ark package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

