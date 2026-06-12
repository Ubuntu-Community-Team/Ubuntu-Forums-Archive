---
title: "Xclient script no longer working"
date: 2008-08-23
forum: General Help
---

### Post by aalinovi on 2008-08-23
Not sure what I did, but the default Xclient script no longer runs. I can choose other window managers and desktop environments but the default tells me I've only been logged in less than 10 seconds and to check the xsessions-error file.
I'd be grateful if someone would look thru that and tell a beginner what the problem might be and how to go about fixing it. Thanks. 
That file reads:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/computer:/tmp/.ICE-unix/5932
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
<stdin>:242:2: error: invalid preprocessing directive #xterm
<stdin>:243:2: error: invalid preprocessing directive #xterm
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...none found
11
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 47828 1219536000 1219488172
evolution-alarm-notify-Message:  Sat Aug 23 20:00:00 2008

evolution-alarm-notify-Message:  Sat Aug 23 06:42:52 2008

Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6052): WARNING **: Unable to add monitor: Not supported
Starting gtk-window-decorator

(gnome-panel:6049): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -42 and height 24

(gnome-panel:6049): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -42 and height 24
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I/O warning : failed to load external entity "/home/augie/.compiz/session/default0"

---

### Post by margot on 2008-08-26
I have no idea why, but this seems to have fixed a different problem. See the thread:

[http://ubuntuforums.org/showthread.php?p=5670655#post5670655](http://ubuntuforums.org/showthread.php?p=5670655#post5670655)

Any ideas why? Please post on the newer thread.

---

