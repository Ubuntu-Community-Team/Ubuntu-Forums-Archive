---
title: "Ubuntu 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Sanix on 2008-11-02
I've installed the new Ubuntu and got a problem. Gnome hangs after I enter my login information. It hangs for about 2 minutes, here my .xsessionlog:

> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[8228]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Xlib:  extension "XEVIE" missing on display ":0.0".

(at-spi-registryd-wrapper:8309): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(at-spi-registryd-wrapper:8309): atk-bridge-WARNING **: IOR not set.

(at-spi-registryd-wrapper:8309): atk-bridge-WARNING **: Could not locate registry
x-session-manager[8228]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup.
x-session-manager[8228]: atk-bridge-WARNING: IOR not set.
x-session-manager[8228]: atk-bridge-WARNING: Could not locate registry
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
x-session-manager[8228]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
seahorse nautilus module initialized
Initializing nautilus-share extension

(gnome-panel:8398): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
Unable to open desktop file /usr/share/applications/sunbird.desktop for panel launcher: No such file or directory
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

x-session-manager[8228]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC
Throttle level is 0
Failure: Module initalization failed

** (nautilus:8399): WARNING **: Unable to add monitor: Not supported
evolution-alarm-notify-Message: Setting timeout for 30284 1225666800 1225636516
evolution-alarm-notify-Message:  Mon Nov  3 00:00:00 2008

evolution-alarm-notify-Message:  Sun Nov  2 15:35:16 2008



I found workarounds such as use the following boot options
noapictimer and irqpoll. It still hangs but just for 30 seconds now.

What do these options? I guess, I will have less functionality? And the interesting thing is, OpenSuse 11 with gnome works. Do they use another kernel version?

---

### Post by Sanix on 2008-11-02
*push*

Too many people are having this problem but nobody knows what to do. Maybe some Ubuntu guru knows, where the problem could be? Do I need to provide other logfiles?

---

### Post by macabro22 on 2008-11-02
bump

---

### Post by Sanix on 2008-11-04
It has something to do with the NVIDA 177 driver. But on the other hand the same driver works in Opensuse. Are there any modifications in Ubuntu?

---

### Post by macabro22 on 2008-11-04
ops, wrong thread.

---

### Post by Sanix on 2008-11-11
*push*

---

