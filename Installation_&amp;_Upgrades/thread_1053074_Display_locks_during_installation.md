---
title: "Display locks during installation"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by vanderdyken on 2009-01-28
I attempted to install 32 bit Intrepid on an AMD 64 box already running Debian lenny.  All went smoothly until the x-window display opened and froze.

I rebooted to lenny and started ubuntu as a chroot and was able to run apt-get update and apt-get dist-upgrade from a console. When I attemped to open the x-window (/etc/init.d/gdm restart) the Gnome desktop appeared and the froze with a message "Unable to initialize HAL" From the console the command lshal responds:

error: dbus_bus_get: org.freedesktop.Dbus.Error.FileNotFound: failed to connect to socket /var/run/dbus/system_bus_socket  No such file or directory.

Of course from a lenny console lshal responds normally.

I edited lilo.conf and tried to boot directly to Intrepid.  Again the x-window open and froze with no messages, just a splash screen.

Any suggestions?

---

