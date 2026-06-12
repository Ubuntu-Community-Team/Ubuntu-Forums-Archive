---
title: "Belkin Bluetooth USB / Ubuntu 11.10, 64-bit"
date: 2012-04-20
forum: Hardware
---

### Post by Kahoss on 2012-04-20
I follow the instructions to install a Belkin bluetooth USB 

gksu gedit /etc/modprobe.d/blacklist

enter password and add the lines:

blacklist hci_usb

gksu gedit /etc/modules

hci_usb reset=1

I got the following:

(gksu:5113): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5115): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5115): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WD95CW': No such file or directory

(gedit:5115): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5115): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HVR1CW': No such file or directory

(gedit:5115): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Some help ... pleaseeee..... THANKS !!!

---

