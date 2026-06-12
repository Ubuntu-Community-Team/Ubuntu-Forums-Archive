---
title: "Last round of updates freaked out Network Manager"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2009-11-11
It appears to be either a conflict or a regresssion, but the last round of updates did something weird to my network manager.

```

Upgraded the following packages:
apparmor (2.3.1+1403-0ubuntu27) to 2.3.1+1403-0ubuntu27.1
apparmor-utils (2.3.1+1403-0ubuntu27) to 2.3.1+1403-0ubuntu27.1
apport (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.1
apport-gtk (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.1
checkbox (0.8.5) to 0.8.6
checkbox-gtk (0.8.5) to 0.8.6
chromium-browser (4.0.241.0~svn20091108r31403-0ubuntu1~ucd1) to 4.0.242.0~svn20091109r31427-0ubuntu1~ucd1
cups (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-bsd (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-client (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
cups-common (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
evince (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.1
evolution (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-common (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-documentation-en (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
evolution-plugins (2.28.1-0ubuntu1) to 2.28.1-0ubuntu2
gnome-about (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gnome-desktop-data (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gtk2-engines (1:2.18.4-1ubuntu1) to 1:2.18.4-1ubuntu2
gtk2-engines-murrine (0.90.3-1ubuntu1) to 0.90.3-1ubuntu2
libapparmor-perl (2.3.1+1403-0ubuntu27) to 2.3.1+1403-0ubuntu27.1
libapparmor1 (2.3.1+1403-0ubuntu27) to 2.3.1+1403-0ubuntu27.1
libclutter-gtk-0.10-0 (0.10.2-0ubuntu1) to 0.10.2-0ubuntu2
libcups2 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupscgi1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsdriver1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsimage2 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsmime1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libcupsppdc1 (1.4.1-5ubuntu2) to 1.4.1-5ubuntu2.1
libenchant1c2a (1.5.0-0ubuntu2) to 1.5.0-0ubuntu3
libevdocument1 (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.1
libevview1 (2.28.1-0ubuntu1) to 2.28.1-0ubuntu1.1
libgnome-desktop-2-11 (1:2.28.1-0ubuntu2) to 1:2.28.1-0ubuntu3
libgudev-1.0-0 (1:147~-6) to 1:147~-6.1
libhippocanvas-1-0 (0.3.0-1build1) to 1:0.3.0~ppa3
libjline-java (0.9.94-1ubuntu1) to 0.9.94-5~ubuntu1
libnautilus-extension1 (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu2
libpurple-bin (1:2.6.2-1ubuntu7) to 1:2.6.3-1ubuntu1~pidgin1.9.10
libpurple0 (1:2.6.2-1ubuntu7) to 1:2.6.3-1ubuntu1~pidgin1.9.10
libpython2.6 (2.6.4-0ubuntu1) to 2.6.4-0ubuntu2
libudev0 (147~-6) to 147~-6.1
nautilus (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu2
nautilus-data (1:2.28.1-0ubuntu1) to 1:2.28.1-0ubuntu2
protobuf-compiler (2.0.3-2.2ubuntu2) to 2.1.0-1karmic2
python-apport (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.1
python-hippocanvas (0.3.0-1build1) to 1:0.3.0~ppa3
python-problem-report (1.9.3-0ubuntu4) to 1.9.3-0ubuntu4.1
python-protobuf (2.0.3-2.2ubuntu2) to 2.1.0-1karmic2
python-support (1.0.3ubuntu1) to 1.0.3ubuntu2~tj~ppa1k
python2.6 (2.6.4-0ubuntu1) to 2.6.4-0ubuntu2
python2.6-minimal (2.6.4-0ubuntu1) to 2.6.4-0ubuntu2
rhythmbox (0.12.5-0ubuntu4) to 0.12.5-0ubuntu5
udev (147~-6) to 147~-6.1
update-manager (1:0.126.6.1) to 1:0.126.9
update-manager-core (1:0.126.6.1) to 1:0.126.9
xulrunner-1.9.1 (1.9.1.4+nobinonly-0ubuntu0.9.10.1) to 1:1.9.1.1+build1+nobinonly-0ubuntu2~ppa4
xulrunner-1.9.1-gnome-support (1.9.1.4+nobinonly-0ubuntu0.9.10.1) to 1:1.9.1.1+build1+nobinonly-0ubuntu2~ppa4

```

No network information. I'm connected but it doesn't seem like the connection is being monitored. At first got this message. "Service not managed" so I changed 

/etc/NetworkManager/nm-system-settings.conf 

```


main
plugins=ifupdown,keyfile

ifupdown
managed=true

```


This is what    /etc/network/interfaces looks like:

```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

I've been told by my LoCo that it should look like this:

```

auto lo
iface lo inet loopback 

```

but doing this doesn't change anything.I see there is also talk about a bug associated with Network Manager [http://ubuntuforums.org/showthread.php?p=8293692#post8293692](http://ubuntuforums.org/showthread.php?p=8293692#post8293692)

---

