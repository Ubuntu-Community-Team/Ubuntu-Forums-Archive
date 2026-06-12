---
title: "[SOLVED] my nvidia is annoying me"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by mrreality13 on 2007-07-23
Hi All,
Im running 7.04
every time i re boot my pc i have to start from scratch with , "sudo nvidia-settings" to get ny tv out to work (card is a 7600 gs pci-e)
should'nt i have an nvidia settings button in my prefrences tab?
thanx in advance:popcorn:

---

### Post by ibanez88 on 2007-07-23
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Put this in the file:



[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon= StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;




Then restart x.

as taken from [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by dougfractal on 2007-07-23
My guess is that the "save  X configuration" isn't working.
So click "save  X configuration" then "Show preview". Select text.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
sudo gedit /etc/X11/xorg.conf
```
paste text and save.

You will need to renable Desktop effects, as  nvidia-settings removes these.

---

### Post by ibanez88 on 2007-07-23
also from [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

If "nvidia-settings" loses its settings every time you reboot Get to the following menus (if you use GNOME): System -> Preferences -> Sessions -> Startup Programs

Then click on "Add"

And insert this command:

nvidia-settings --load-config-only



But I would try dougfractal's suggestion first as it does seem odd that it wouldn't just save the settings to your xorg.conf

---

### Post by mrreality13 on 2007-07-23
thanx all:guitar::guitar:
dougfractal's suggestion worked well

---

