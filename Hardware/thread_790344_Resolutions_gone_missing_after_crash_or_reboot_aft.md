---
title: "Resolutions gone missing after crash or reboot after update"
date: 2008-05-11
forum: Hardware
---

### Post by Pettman on 2008-05-11
Yesterday after a reboot caused by warzone 2100 locking up xorg suddenly refused to show 1280×1024, which has worked with for me for years under ubuntu. Everything else seems to be working fairly the same as before.
My gfx-card is a HIS Radeon 9600 Pro using the open-source drivers (the fglrx have never worked well for me), the rest of the system is a AMD Athlon XP 2800+, 1024 MiB of PC3200 RAM, chipsets from VIA (vt600 and something else). In order to make the os drivers work I've been forced to force agp-mode 4.
I've got two theories about what have happened:
1. The crash broke my Radeon 9600 Pro in some way (not that likely)
2. One of the updated packages messed up something with the graphics drivers or xorg.
The packages updated between the last working boot and the reboot after the crash were:```

bash (3.2-0ubuntu16) to 3.2-0ubuntu17
evolution (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
evolution-common (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
evolution-data-server (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
evolution-data-server-common (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
evolution-plugins (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
friendly-recovery (0.1) to 0.1.2
gcc-3.3-base (1:3.3.6-15ubuntu4) to 1:3.3.6-15ubuntu6
gksu (2.0.0-5ubuntu2) to 2.0.0-5ubuntu3
gstreamer0.10-plugins-good (0.10.7-3) to 0.10.7-3ubuntu0.1
gtk2-engines-pixbuf (2.12.9-3ubuntu3) to 2.12.9-3ubuntu4
libcamel1.2-11 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libebook1.2-9 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libecal1.2-7 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libedata-book1.2-2 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libedata-cal1.2-6 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libedataserver1.2-9 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libedataserverui1.2-8 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libegroupwise1.2-13 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libexchange-storage1.2-3 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libgdata-google1.2-1 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libgdata1.2-1 (2.22.1.1-0ubuntu1) to 2.22.1.1-0ubuntu2
libgtk2.0-0 (2.12.9-3ubuntu3) to 2.12.9-3ubuntu4
libgtk2.0-bin (2.12.9-3ubuntu3) to 2.12.9-3ubuntu4
libgtk2.0-common (2.12.9-3ubuntu3) to 2.12.9-3ubuntu4
libmysqlclient15off (5.0.51a-3ubuntu5) to 5.0.51a-3ubuntu5.1
libqt4-assistant (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-core (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-dbus (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-designer (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-gui (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-network (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-opengl (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-script (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-svg (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-test (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqt4-xml (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqtcore4 (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libqtgui4 (4.4.0-1ubuntu1~hardy1) to 4.4.0-1ubuntu3~hardy1
libspeex1 (1.1.12-3) to 1.1.12-3ubuntu0.8.04.1
libstdc++5 (1:3.3.6-15ubuntu4) to 1:3.3.6-15ubuntu6
linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.35) to 2.6.24.12-17.36
linux-restricted-modules-common (2.6.24.12-17.35) to 2.6.24.12-17.36
mysql-common (5.0.51a-3ubuntu5) to 5.0.51a-3ubuntu5.1
python2.5 (2.5.2-2ubuntu4) to 2.5.2-2ubuntu5
python2.5-minimal (2.5.2-2ubuntu4) to 2.5.2-2ubuntu5
transmission-common (1.06-0ubuntu4) to 1.06-0ubuntu5
transmission-gtk (1.06-0ubuntu4) to 1.06-0ubuntu5
update-manager (1:0.87.26) to 1:0.87.27
update-manager-core (1:0.87.26) to 1:0.87.27
wine (0.9.61~winehq0~ubuntu~8.04-1) to 1.0~rc1~winehq0~ubuntu~8.04-1
```

EDIT: I've managed to get it back working :) I had to manually add some resolutions to the xorg.conf.

---

