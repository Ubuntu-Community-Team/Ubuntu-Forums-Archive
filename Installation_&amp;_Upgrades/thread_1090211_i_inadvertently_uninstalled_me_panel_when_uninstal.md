---
title: "i inadvertently uninstalled me panel when uninstalling avant window manager..."
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by sookun on 2009-03-08
hi there

i managed to get online and i downloaded the package but i need to go to terminal to to the cd and ./configure and i dnt have the link to terminal and the key alt+f2 isnt  working... any .deb package???

---

### Post by Partyboi2 on 2009-03-08
Try booting into recovery and after login try install ubuntu-desktop package this should pull in any missing packages including gnome-panel.
```
apt-get install ubuntu-desktop
```

---

### Post by dzark on 2009-03-08
i keep a copy of it on my usbkey for this exact reason :)


rapidshar is a link to gp.desktop that is a link to gnomepanel program incase you havn't uninstalled it, just removed it.. then attached file is the .deb 

wont let me attach .desktop files? hence the rapidshare

[http://rapidshare.com/files/206704319/gp.desktop.html](http://rapidshare.com/files/206704319/gp.desktop.html)

---

### Post by sookun on 2009-03-08
thkss buddies..

i got this error while installing the deb
ill reboot and enter recovery mode

/tmp/gnome-panel_2.24.1-0ubuntu2_i386-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by dzark on 2009-03-08
try ```
sudo dpkg -i gnome-panel_2.24.1-0ubuntu2_i386-2.deb
```

---

### Post by sookun on 2009-03-08
thks window maker was around...phew..got accessed to synaptics from over there then installed gnome-panel..

---

