---
title: "Nvidia-glx settings problem"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by yootje on 2005-08-22
I have an onboard Nvidia Gforce 440 MX, so I tried to install nvidia-glx, but I have a problem to set it up:

> 
yorian@phobera:~ $ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
yorian@phobera:~ $ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Now I'm a newbie and I follw the instructions of this site: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver) but I'm not sure what to do now.

My current xorg.conf is now this:

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection


Should I change it to:

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection


? Or should I do something else?

And what to do with that .desktop file, It's not empty.

---

### Post by coolclassic on 2005-08-22
Go ahead change the driver section to nvidia.

---

### Post by yootje on 2005-08-22
Hm, well that didn't work :P

X closes and when I re-edit xorg.conf from nvidia back to nv, it works fine (except I play games in 1fp and my screen acts funny as it did before).

---

### Post by coolclassic on 2005-08-22
Did you try the md5sum command if not try it then follow the instructions given in the ubuntuguide.

md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum

---

### Post by yootje on 2005-08-22
[QUOTE=coolclassic]Did you try the md5sum command if not try it then follow the instructions given in the ubuntuguide.

md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum[/QUOTE]
And that worked! :) The .desktop file is still empty, but I try it anyway, I don't know if that's normal?

---

### Post by yootje on 2005-08-22
When I try it, the screen is black and blinks a lot and than there is an error from X saying libdria. is unresolved (that's not the exact version, but it was something like that, sorry).

---

### Post by coolclassic on 2005-08-22
You have to edit the dektop file your self. Open up the file by using the following command>

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

and then copy and paste the following into the file and save.

------copy----------

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

-------copy------------

---

### Post by yootje on 2005-08-22
[QUOTE=coolclassic]You have to edit the dektop file your self. Open up the file by using the following command>

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

and then copy and paste the following into the file and save.

------copy----------

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

-------copy------------[/QUOTE]
That's exactly what I did ;)

---

### Post by yootje on 2005-08-22
Ok, what I did now:

> 
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

Only with the md5-checksum-thing)

ctrl-alt backspace

I saw the libdri.a error again and no splash screen, but this error:

(EE) Failed to initialize GLX extensions (NVIDIA X driver not found) 

Couldn't start Gnome

When I edited nvidia in xorg.conf back to nv, it worked again

---

