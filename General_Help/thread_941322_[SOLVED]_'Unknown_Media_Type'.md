---
title: "[SOLVED] 'Unknown Media Type'"
date: 2008-10-08
forum: General Help
---

### Post by DougieFresh4U on 2008-10-08
I seem to get the following output from terminal quite often also the 'parse error thingy' was a new one today. Can some one please explain what the two things mean and what (if there is) is the way to correct
Thanks
```
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up apport-gtk (0.117) ...

Setting up binutils (2.18.92.20081003-0ubuntu2) ...

Setting up libbluetooth3 (4.12-0ubuntu1) ...

Setting up bluez-cups (4.12-0ubuntu1) ...
Setting up dbus (1.2.4-0ubuntu1) ...
The system user `messagebus' already exists. Exiting.
 * Reloading system message bus config...                                                    [ OK ] 

Setting up bluez-gnome (1.8-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/bluetooth-applet.desktop ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up capplets-data (1:2.24.0.1-0ubuntu3) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `??????????? ?????? ;gtk-theme-selector.desktop,???????????? ??????????? ???;default-applications.desktop,??????????? ????;gnome-cups-manager.desktop]' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'



```
solved via fresh install,** again**

---

### Post by Partyboi2 on 2008-10-09
Looks like you could have struck this bug 
[https://bugs.launchpad.net/ubuntu/+bug/268956](https://bugs.launchpad.net/ubuntu/+bug/268956)
[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/193325)
[https://bugs.launchpad.net/gnome-control-center/+bug/276272](https://bugs.launchpad.net/gnome-control-center/+bug/276272)

---

