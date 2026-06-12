---
title: "messed up my eee-controlinstallation"
date: 2009-05-08
forum: Hardware
---

### Post by Giles on 2009-05-08
hey, first of all hope i'm posting this in the right place.

anyway, i just upgraded my easy peasy installation to jaunty using an alternate cd. so my old ibex eee-control daemon was still installed but it didn't work anymore. at this time i didn't realize that i could uninstall the package via synaptic, so being the idiot that i am i busted out the:
sudo su
and tried to uninstall it manually by using rm and rm -r on the list of included files, i think i removed a directory that i wasn't supposed to, anyway this is the list:
./
etc/
etc/init.d/
etc/init.d/eee-control
etc/xdg/
etc/xdg/autostart/
etc/xdg/autostart/eee-control-tray.desktop
etc/dbus-1/
etc/dbus-1/system.d/
etc/dbus-1/system.d/eee-control-daemon.conf
usr/
usr/share/
usr/share/applications/
usr/share/applications/eee-control-tray.desktop
usr/share/pyshared-data/
usr/share/pyshared-data/eee-control
usr/share/locale/
usr/share/locale/hu/
usr/share/locale/hu/LC_MESSAGES/
usr/share/locale/hu/LC_MESSAGES/eee-control.mo
usr/share/locale/es/
usr/share/locale/es/LC_MESSAGES/
usr/share/locale/es/LC_MESSAGES/eee-control.mo
usr/share/locale/ca/
usr/share/locale/ca/LC_MESSAGES/
usr/share/locale/ca/LC_MESSAGES/eee-control.mo
usr/share/locale/fr/
usr/share/locale/fr/LC_MESSAGES/
usr/share/locale/fr/LC_MESSAGES/eee-control.mo
usr/share/locale/de/
usr/share/locale/de/LC_MESSAGES/
usr/share/locale/de/LC_MESSAGES/eee-control.mo
usr/share/eee-control/
usr/share/eee-control/eee-icon.png
usr/share/eee-control/eee-control.conf
usr/lib/
usr/lib/python2.6/
usr/lib/python2.6/dist-packages/
usr/lib/python2.6/dist-packages/EeeControl/
usr/lib/python2.6/dist-packages/EeeControl/actions.py
usr/lib/python2.6/dist-packages/EeeControl/config.py
usr/lib/python2.6/dist-packages/EeeControl/tray.py
usr/lib/python2.6/dist-packages/EeeControl/ioport.so
usr/lib/python2.6/dist-packages/EeeControl/models.py
usr/lib/python2.6/dist-packages/EeeControl/__init__.py
usr/lib/python2.6/dist-packages/EeeControl/she.py
usr/lib/python2.6/dist-packages/EeeControl/utils.py
usr/lib/python2.6/dist-packages/EeeControl/ichsmbus.py
usr/lib/python2.6/dist-packages/EeeControl/daemonize.py
usr/lib/python2.6/dist-packages/eee_control-0.9.1.egg-info
usr/bin/
usr/bin/eee-control-query.sh
usr/bin/eee-control-tray
usr/bin/eee-control-setup.sh
usr/bin/eee-control-daemon
usr/bin/eee-dispswitch.sh
usr/src/
usr/src/eeepc-laptop-20090415/
usr/src/eeepc-laptop-20090415/dkms.conf
usr/src/eeepc-laptop-20090415/eeepc-laptop.c
usr/src/eeepc-laptop-20090415/Makefile

so now when i try to install the new eee-control i get this:
[[IMG]http://img10.imageshack.us/img10/3725/screenbsp.png[/IMG]](http://img10.imageshack.us/my.php?image=screenbsp.png)

i'm really sorry for being a noob and ******* this up thanks in advance if anyone actually bothers to help me. and yeah i'm an idiot for sudo su-ing and then going crazy with the rm command...

---

### Post by aysiu on 2009-05-08
Maybe something like ```
sudo apt-get install --reinstall linux-image-2.6.27-8-eeepc
``` might help. The problem is that exists in only the Intrepid version of the Array kernel repositories. The Jaunty ones have a different name and are still in testing:
[http://array.org/ubuntu/](http://array.org/ubuntu/)

---

### Post by Giles on 2009-05-10
i reinstalled it but i get the same error. it seems that updating the kernel does not update the source files. oh well it was worth a shot.

maybe i should just clean reinstall intrepid? thanks anyway

edit: sudo apt-get install linux-headers-$(uname -r) build-essential fixed it. sweet

---

