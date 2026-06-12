---
title: "First start-up of Ubuntu halts immediately after log-in"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Arancaytar on 2009-02-21
Hi,

I'm using a Laptop (Samsung, 2 GHz, 512 MB RAM). I've installed Ubuntu 8.10 with the standard desktop CD, using a 15 GB primary partition for the system (mounted on /) and a 5 GB logical volume as swap space. I also opted to import user data from the existing XP Home system (Firefox profile, documents and desktop settings).

The installation finished successfully. After rebooting and starting Ubuntu for the first time, I get as far as the login screen. After logging in with my normal user account, the system just halts.

The default beige background is already displayed (but not the default wallpaper), and the mouse cursor is visible and movable. For a few seconds, the LED on my laptop indicates disk activity, but this stops. I've waited almost one hour to be sure it was stuck.

---

Starting up in recovery mode, I have used all standard options offered: 
- fsck to confirm that the (newly created) Ext3 system volume was okay, 
- dpkg to check for broken packages, which appeared to confirm that all packages were properly installed and up-to-date
- xfix, which appeared to reset my X configuration to default values after creating a backup.
- the root shell works. I have successfully set up the network, gateway and nameservers as root, pinged inside and outside the local network, and even built a manual HTTP connection to google.com (couldn't manage to install lynx via apt-get, unfortunately).

However, even after doing these four things, the system still gets stuck immediately after the login screen.

While writing this, I realize I haven't yet tried logging in as root in the graphical interface (instead of the shell in recovery mode) or logging in with my normal account while in the root shell. I'll try that afterward.

Can I get any pointers for what else to try next? Thanks very much! :)

----

Update: root is blocked from logging in to the desktop, but I was able to create a new user and discover something interesting.

When first logging in with a newly created user, the system does not get stuck immediately, but first plays a startup sound. Then the screen turns black, the mouse cursor becomes a disk, and the system is stuck. This happened once with my original user and once with the second user, but only on the first attempt.

On subsequent logins with that user, the system gets stuck before playing the intro sound.

---

### Post by Arancaytar on 2009-02-22
To investigate the difference between the first login and any subsequent logins with the same user, I experimented with deleting several user files generated on start-up.

I have found what makes the difference between the login sound being
played on the first login, and the system halting before on subsequent logins:

Namely, ~/.gstreamer-0.10/registry.i486.bin is created the first time.

If I delete this file, the system will regenerate it and again play the sound
before freezing; if I then log in again while the file exists, the system will freeze without playing the sound. That info might help in identifying which part of the startup sequence causes the crash.

The file is 219 kB, and contains a lot of ASCII text between the binary stuff
that looks like Video or animation data. I have uploaded the file to [http://stuff.ermarian.net/arancaytar/txt/registry.i486.bin](http://stuff.ermarian.net/arancaytar/txt/registry.i486.bin)

I'm beginning to suspect there is something wrong with my sound or video
drivers. I should try switching off the launch animation. I'll also google for this file and see what creates it.

Here is a copy of my ~/.xsession-errors file:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to
/etc/X11/xinit/xinput.d/default.
x-session-manager[5362]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
x-session-manager[5362]: WARNING: Application 'gnome-wm.desktop' failed to
register before timeout
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:5593): WARNING **: Unable to add monitor: Not supported
Starting gtk-window-decorator
x-session-manager[5362]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken
(jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
starting HAL detection for ac adaptors...found
/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ADP1
Throttle level is 5

```

Thanks so much for help! :)

---

### Post by Arancaytar on 2009-03-05
... anyway, I was fortunately able to get some tips elsewhere and work around the problem, which I'll post here.

The problem seemed to be caused by compiz, so I uninstalled it and replaced it with metacity in the /desktop/gnome/applications/window_manager/default key of .gconf. There seem to be some lingering configuration problems (I cannot enable any visual effects), but at least I have been able to launch the desktop and use it fairly well, so that problem is solved now.

---

### Post by Yashiro on 2009-03-05
Compiz IS the Visual Effects. It's just not made very clear on the interface.

---

### Post by Arancaytar on 2009-03-06
In that case, I can only guess that my somewhat elderly graphics card (Intel 82845G/GL/GE/PE/GV Graphics Controller) isn't supported, or that there is some conflict. Anyway, I can live without the visual effects, seeing as my single CPU and by today's standards tiny RAM are already busy enough.

---

