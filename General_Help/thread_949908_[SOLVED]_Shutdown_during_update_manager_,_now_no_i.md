---
title: "[SOLVED] Shutdown during update manager , now no internet or mounting"
date: 2008-10-16
forum: General Help
---

### Post by sigma150 on 2008-10-16
My computer shutdown while update manager was running(pulled power cord). When I restarted my computer the internet stopped working and I can no longer mount any device. 

When I run 'network -admin' in the terminal it says "The permission on setuid helper is not correct" and when trying to mount a usb thumb drive it says 'Error org.freedesktop.Dbus.Error.AcessedDenied'. 

And oddly enough when I press the power button on the front of my computer it no longer shuts down the device.

Thanks for any help

---

### Post by geirha on 2008-10-16
Boot the live CD, mount your root partition at /media/disk, then run in a terminal: 
```
sudo chroot /media/disk
``` 
/media/disk should now be / in that terminal. Try running ```
dpkg --configure -a
``` to finish configure packages that did not get configured properly before the power outage.

---

### Post by sigma150 on 2008-10-16
thanks for the quick response...

when it type 'sudo chroot /media/disk' I get:

Setting up dbus (1.1.20-1ubuntu3.1) ...
The user `messagebus' already exists. Exiting.
/var/lib/dpkg/info/dbus.postinst: 24: cannot create /dev/null: Permission denied
/var/lib/dpkg/info/dbus.postinst: 65: cannot create /dev/null: Permission denied
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 dbus-x11

---

### Post by geirha on 2008-10-17
Try running

```
aptitude safe-upgrade
``` in the same way as dpkg --configure -a

---

### Post by sigma150 on 2008-10-17
same deal as last time I get:

root@ubuntu:/# aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libboo2.0-cil 
The following packages have been kept back:
  openmovieeditor 
The following partially installed packages will be configured:
  dbus dbus-x11 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 1532kB will be freed.
Do you want to continue? [Y/n/?] y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 270356 files and directories currently installed.)
Removing libboo2.0-cil ...
/usr/share/cli-common/policy-remove: 13: cannot create /dev/null: Permission denied
dpkg: error processing libboo2.0-cil (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libboo2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up dbus (1.1.20-1ubuntu3.1) ...
The user `messagebus' already exists. Exiting.
/var/lib/dpkg/info/dbus.postinst: 24: cannot create /dev/null: Permission denied
/var/lib/dpkg/info/dbus.postinst: 65: cannot create /dev/null: Permission denied
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 dbus-x11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

### Post by geirha on 2008-10-18
Hm, seems the chroot environment should be set up more properly for aptitude to work. However, all the packages should've been downloaded by now, so boot into your system normally, and run ```
sudo aptitude safe-upgrade
``` and see if that works better.

---

### Post by sigma150 on 2008-10-18
Thank you

---

