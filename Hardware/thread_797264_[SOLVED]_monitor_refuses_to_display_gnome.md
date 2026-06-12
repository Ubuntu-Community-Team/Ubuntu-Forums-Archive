---
title: "[SOLVED] monitor refuses to display gnome"
date: 2008-05-17
forum: Hardware
---

### Post by Nycticorax on 2008-05-17
I've been happily running gnome under Hardy (8.04) on my laptop, and displaying it on an external widescreen monitor. That has been fine. Yesterday, the monitor suddenly went blank, and subsequently it has refused to display gnome. Specifically, it displays the ubuntu login screen, and then comes up with an "out of range" message against a blank screen. In my .xsession-errors (full contents below) I find the line

** (nautilus:7942): WARNING **: Unable to add monitor: Not supported

My monitor *does* happily display ubuntu hardy running an alternative X window manager (ion3).

Any ideas how to fix/investigate this and what happened to it yesterday?

I've tried messing about with the screen resolution control in preferences -> screen resolution but to no avail.

In case it isn't coincidence, the screen went blank while I was plotting an image in a statistical package. It may have been somewhat processor / graphics card intensive if that's relevant.

Thanks for any help,

Dan

.xsession-errors follows:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/Tichodroma:/tmp/.ICE-unix/7847
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
seahorse nautilus module initialized
Initializing nautilus-share extension
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 

** (nautilus:7942): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:7942): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:7942): WARNING **: Can not get _NET_WORKAREA

** (nautilus:7942): WARNING **: Can not determine workarea, guessing at layout
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.tx](http://www.gnu.org/licenses/gpl.tx)
t

Initialising tracker...

** (trackerd:8046): WARNING **: Tracker daemon is already running - attempting to run in readonly mode
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...9
2008-05-17 09:49:45 3420 11381 1694
found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC
Throttle level is 0

** (nautilus:7942): WARNING **: Unable to add monitor: Not supported
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
2008-05-17 09:50:15 3270 11547 1800
2008-05-17 09:50:45 3270 11547 1482
ERROR: could not open /proc/asound/cards: [Errno 2] No such file or directory: '/proc/asound/cards'
WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

  PID TTY          TIME CMD
  PID TTY          TIME CMD
 7922 ?        00:00:00 pulseaudio
2008-05-17 09:51:15 3220 11492 1800
2008-05-17 09:51:45 3220 11492 1588
2008-05-17 09:52:15 3220 11492 1588
2008-05-17 09:52:45 3220 11492 1588

---

### Post by Nycticorax on 2008-05-19
OK I have solved this with lots of random messing about with the gnome screen resolution control thing. Sorry for the noise.

---

