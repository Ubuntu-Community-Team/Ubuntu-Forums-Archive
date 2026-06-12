---
title: "Behind Firewall from Hell, can't upgrade"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by goldsby on 2009-05-18
Upgrade manager stalls forever on first file.

However, I can navigate to archive sites in my browser and download .deb files "by hand".

How can I accomplish an upgrade?

Thanks,
--Mike

---

### Post by coffeecat on 2009-05-18
Normally the update manager would give you an error message to tell you what's (not) going on, but let's see if we can get one. Open a terminal and do these two commands:

```
sudo apt-get update
sudo apt-get upgrade
```

If you get any errors, post them. Or if the process stalls, post the few lines just before the stall. And if things work out just fine, then you've got yourself an upgraded system and you'll have to wait to next time to see how the update manager works.

---

### Post by goldsby on 2009-05-19
Here's the output from 'sudo apt-get update':

Ign [http://packages](http://packages) gutsy Release.gpg
Ign [http://packages](http://packages) gutsy/free Translation-en_US
Ign [http://packages](http://packages) gutsy/non-free Translation-en_US
Ign [http://packages](http://packages) gutsy Release
Ign [http://packages](http://packages) gutsy/free Packages
Ign [http://packages](http://packages) gutsy/non-free Packages
Err [http://packages](http://packages) gutsy/free Packages
  503 Service Unavailable [IP: 134.252.97.2 80]
Err [http://packages](http://packages) gutsy/non-free Packages
  503 Service Unavailable [IP: 134.252.97.2 80]
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  404 Not Found [IP: 134.252.97.1 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://packages/medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz](http://packages/medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz)  503 Service Unavailable [IP: 134.252.97.2 80]
Failed to fetch [http://packages/medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages/medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  503 Service Unavailable [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 134.252.97.1 80]
Fetched 1B in 9s (0B/s)
Reading package lists...
E: Some index files failed to download, they have been ignored, or old ones used instead.


-------------------------------------------------------------------

And here's the output from sudo apt-get upgrade:


~ Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  gimp gimp-data gimp-python linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ntfs-3g ssl-cert
The following packages will be upgraded:
  bind9-host compiz compiz-core compiz-fusion-plugins-extra compiz-gnome
  compiz-plugins cpio cupsys cupsys-bsd cupsys-client cupsys-common dbus
  dnsutils esound-common hpijs hplip hplip-data irb1.8 language-pack-en
  language-pack-gnome-en libbind9-30 libcupsimage2 libcupsys2 libdbus-1-3
  libdecoration0 libdns32 libesd-alsa0 libexif12 libfreetype6 libgimp2.0
  libisc32 libisccc30 libisccfg30 liblwres30 libpcre3 libpcrecpp0
  libpoppler-glib2 libpoppler2 libpq5 libreadline-ruby1.8 libruby1.8
  libtheora0 libtiff4 libxml2 libxml2-utils libxslt1.1 linux-libc-dev
  openssh-client openssh-server poppler-utils python-apt python-libxml2
  python2.5 python2.5-minimal rdesktop rdoc1.8 ri1.8 ruby1.8 ssh-askpass-gnome
  tzdata xsltproc yelp
62 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 31.4MB of archives.
After unpacking 1536kB of additional disk space will be used.
Do you want to continue [Y/n]? WARNING: The following packages cannot be authenticated!
  python-apt libcupsys2 libtiff4 libcupsimage2 libdbus-1-3 libfreetype6
  libxml2 libpoppler2 poppler-utils cupsys-common cupsys hplip hplip-data
  language-pack-en language-pack-gnome-en python2.5 python2.5-minimal tzdata
  cpio libisc32 libdns32 libisccc30 libisccfg30 libbind9-30 liblwres30
  bind9-host dnsutils openssh-server openssh-client libdecoration0
  compiz-gnome compiz-plugins libxslt1.1 compiz-core
  compiz-fusion-plugins-extra compiz cupsys-bsd cupsys-client dbus
  esound-common hpijs libruby1.8 ruby1.8 libreadline-ruby1.8 irb1.8 libexif12
  libgimp2.0 libpcre3 libpcrecpp0 libpoppler-glib2 libpq5 libtheora0
  libxml2-utils linux-libc-dev python-libxml2 rdesktop ri1.8 rdoc1.8
  ssh-askpass-gnome xsltproc yelp libesd-alsa0
Install these packages without verification [y/N]? Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python-apt 0.7.3.1ubuntu4.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsys2 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libcupsys2 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libtiff4 3.8.2-7ubuntu2.1
  404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libcupsimage2 1.3.2-1ubuntu7.8 404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libdbus-1-3 1.1.1-3ubuntu4.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libfreetype6 2.3.5-1ubuntu4.7.10.1
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libpoppler2 0.6.4-1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libxml2 2.6.30.dfsg-2ubuntu1.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main poppler-utils 0.6.4-1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-common 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-common 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main hplip 2.7.12-0ubuntu2~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main hplip-data 2.7.12-0ubuntu2~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-en 1:7.10+20080704
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-en 1:7.10+20080704
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5 2.5.1-5ubuntu5.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main python2.5 2.5.1-5ubuntu5.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python2.5-minimal 2.5.1-5ubuntu5.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main python2.5-minimal 2.5.1-5ubuntu5.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main tzdata 2008h-0ubuntu0.7.10.1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cpio 2.8-1ubuntu2.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cpio 2.8-1ubuntu2.2
                                                                                                                  41,3   404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libisc32 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libisc32 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libdns32 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libdns32 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libisccc30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libisccc30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libisccfg30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libisccfg30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libbind9-30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libbind9-30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main liblwres30 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main bind9-host 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main dnsutils 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main dnsutils 1:9.4.1-P1-3ubuntu2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-server 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-server 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-client 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libdecoration0 1:0.6.2+git20071119-0ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-client 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main compiz-gnome 1:0.6.2+git20071119-0ubuntu1~gutsy1  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main compiz-plugins 1:0.6.2+git20071119-0ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libxslt1.1 1.1.21-2ubuntu2.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libxslt1.1 1.1.21-2ubuntu2.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main compiz-core 1:0.6.2+git20071119-0ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main compiz-fusion-plugins-extra 0.6.0+git20071121-0ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main compiz 1:0.6.2+git20071119-0ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-bsd 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-bsd 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main cupsys-client 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-client 1.3.2-1ubuntu7.8
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main dbus 1.1.1-3ubuntu4.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main dbus 1.1.1-3ubuntu4.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main esound-common 0.2.38-0ubuntu4.1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main hpijs 2.7.12+2.7.12-0ubuntu2~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libruby1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libruby1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ruby1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main ruby1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe libreadline-ruby1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe libreadline-ruby1.8 1.8.6.36-1ubuntu3.3
   404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe irb1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe irb1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libexif12 0.6.16-1ubuntu0.1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libexif12 0.6.16-1ubuntu0.1
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libgimp2.0 2.4.6-1ubuntu1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libpcre3 7.4-0ubuntu0.7.10.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libpcre3 7.4-0ubuntu0.7.10.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libpcrecpp0 7.4-0ubuntu0.7.10.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libpcrecpp0 7.4-0ubuntu0.7.10.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libpoppler-glib2 0.6.4-1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libpq5 8.3.3-1~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main libtheora0 1.0~beta2-2~gutsy1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libxml2-utils 2.6.30.dfsg-2ubuntu1.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libxml2-utils 2.6.30.dfsg-2ubuntu1.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main linux-libc-dev 2.6.22-15.59
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-libc-dev 2.6.22-15.59
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main python-libxml2 2.6.30.dfsg-2ubuntu1.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main python-libxml2 2.6.30.dfsg-2ubuntu1.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main rdesktop 1.5.0-2ubuntu0.1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://secur](http://secur)  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe ri1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe ri1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe rdoc1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe rdoc1.8 1.8.6.36-1ubuntu3.3
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.6
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main xsltproc 1.1.21-2ubuntu2.2
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main xsltproc 1.1.21-2ubuntu2.2
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main yelp 2.20.0-0ubuntu3.1
  404 Not Found [IP: 134.252.97.1 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main yelp 2.20.0-0ubuntu3.1
  404 Not Found [IP: 134.252.97.2 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libesd-alsa0 0.2.38-0ubuntu4.1
  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.3.1ubuntu4.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.3.1ubuntu4.2_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.8_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-7ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-7ubuntu2.1_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.8_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.1.1-3ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.1.1-3ubuntu4.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.7.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.5-1ubuntu4.7.10.1_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/lFailed](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/lFailed) to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.8_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.8_all.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.8_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.12-0ubuntu2~gutsy1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.12-0ubuntu2~gutsy1_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080704_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080704_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080704_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080704_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008h-0ubuntu0.7.10.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008h-0ubuntu0.7.10.1_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.8-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.8-1ubuntu2.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc32_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc32_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns32_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns32_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg30_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg30_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-30_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-30_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres30_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres30_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.4.1-P1-3ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.4.1-P1-3ubuntu2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.6_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.6_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.21-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.21-2ubuntu2.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-extra/compiz-fusion-plugins-extra_0.6.0+git20071121-0ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-extra/compiz-fusion-plugins-extra_0.6.0+git20071121-0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.6.2+git20071119-0ubuntu1~gutsy1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.6.2+git20071119-0ubuntu1~gutsy1_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.8_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.8_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.1.1-3ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.1.1-3ubuntu4.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.38-0ubuntu4.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.38-0ubuntu4.1_all.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.12+2.7.12-0ubuntu2~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.12+2.7.12-0ubuntu2~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.36-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.36-1ubuntu3.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.36-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.36-1ubuntu3.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/libreadline-ruby1.8_1.8.6.36-1ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/libreadline-ruby1.8_1.8.6.36-1ubuntu3.3_i386.deb)  404 Not Found [IP: 134.252.Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.4.6-1ubuntu1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.4.6-1ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.3-1~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.3-1~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.0~beta2-2~gutsy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.0~beta2-2~gutsy1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-15.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-15.59_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.3_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-2ubuntu0.1_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/ri1.8_1.8.6.36-1ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/ri1.8_1.8.6.36-1ubuntu3.3_all.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/rdoc1.8_1.8.6.36-1ubuntu3.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/r/ruby1.8/rdoc1.8_1.8.6.36-1ubuntu3.3_all.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.6_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.21-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.21-2ubuntu2.2_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.20.0-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.20.0-0ubuntu3.1_i386.deb)  404 Not Found [IP: 134.252.97.2 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd-alsa0_0.2.38-0ubuntu4.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd-alsa0_0.2.38-0ubuntu4.1_i386.deb)  404 Not Found [IP: 134.252.97.1 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
~

---

### Post by NetworkGuy on 2009-05-19
Is this a home router/firewall you are talking about?   I have a Linksys WRT54G that will take only trickle updates through (300-400 bytes/sec), but I can torrent and surf and download at full speed.

(Gotta get a new router)

---

### Post by coffeecat on 2009-05-19
Ah, you didn't say you were running Gutsy. That's no firewall from hell. That's an obsoleted version of Ubuntu. The reason you can't upgrade is that it's no longer supported. All packages have been withdrawn from the repositories.

Sorry. You'll have to upgrade or reinstall with a supported version.

---

### Post by goldsby on 2009-05-19
No, this is a firewall at a company that stresses security.

---

### Post by coffeecat on 2009-05-19
Did you see my post about Gutsy no longer supported? We posted more or less simultaneously. More information for you, including links for upgrading:

[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

---

### Post by goldsby on 2009-05-19
Woops.
This is a highly tailored system that I put a lot of effort into configuring. I hate to think of starting from scratch again.  Are copies of the Gutsy archives available from anyone, anywhere in the world?

---

### Post by cariboo on 2009-05-19
Fortunately, the gutsy archives are still available [here]("http:///old-releases.ubuntu.com").

---

### Post by goldsby on 2009-05-19
Whew.
So do I download and burn an iso image of 7.10, update against it, then upgrade to Hardy?

---

