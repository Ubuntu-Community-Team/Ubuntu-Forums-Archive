---
title: "x server no go.  I get a console login prompt only.  gdm missing."
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Matt Damon on 2009-03-27
Upon booting up i get this

Ubuntu 8.10 Pikachu tty1

Pikach login:

I had problems with my previous Hardy install which was dual boot, Windows xp on one drive, Hardy on the other so I did a clean install from a new 'live cd' of Ibex over top of the old install, intent was to do away with Windows completely. Yay. Deal to the old baggage.

Anyway all went well for a few hours, then I started migrating data and deleting files of the old Windows drive...  Maybe there was something i overlooked in the previous dual boot / partitioning...and/or I deleting sometihng

anyway, this is what i am getting.

I go to recovery menu.

try to repair x server

strict.pm did not return a true value at /usr/share/debconf/frontend line 5.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 5.
Warning: Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

<<enter>>.

The X server is now disabled. Restart GDM when it is configured correctly

/etc/x11/xorf.conf/

I checked my xorf.conf

Section "Device"
               Identifier    "Configured Video Device"
EndSection

Section "Monitor"
              Identifier       "Configured Monitor"
End Section

Section "Screen"
              Identifier        "Default Screen"
              Monitor          "Configured Monitor"
              Device           "Configured Video Device"
End Section


Tried to run gdm.   
root@Pikachu:/etc/init.d# gdm
Found that ...

The program 'gdm' is not installed.  You can install it by typgin: apt-get install gdm
bash gdm: command not found
root@Pikachu:etc/init.d# apt-get install gdm
Reading package lists... Done
Building dependancy tree
Reading state information... Done
Package gdm is not avialable, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package gdm has no installation candidate.


Think I am on the right track?

I'm stuck tho...   I'd have no problem doing a clean install again, but I made the mistake of copying all my user data over to the new drive.  Oh dear.

---

### Post by GeeZor on 2009-03-27
did you do an:
```
sudo apt-get update
sudo apt-get upgrade
```

make sure /etc/apt/sources.list holds the entry's you need.

After that, check out if gdm is available:
```
sudo apt-cache search gdm
```

This should show some hits.

What does startx do?
```
startx
```
Did you try to reconfigure xserver-xorg ?
```
sudo dpkg-reconfigure xserver-xorg
```

if all fails, just to get things going install fluxbox
```
sudo apt-get install fluxbox
```

Let me know how things turn out.. will be available today to help out.

---

### Post by Matt Damon on 2009-03-27
Hi GeeZor, thanks for taking the time and helping.

Ran update and upgrade.   Did heaps, loads of updates.
(Not sure what entrys to look for in /etc/apt/sources.list...  but there were plenty of options in there deb and deb-src http nz.archive.ubuntu.com and so on and update did work so good I suppose...)

sudo apt-cache serach gdm came up with loads of hits
startx resulted in my desktop look coming up yay!,looks normal.
 An error window popped up "The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwithApplet"   Do you want to delete the applet from your configuration.  
I did not delete.

I ran update manager...
I restarted, interestingly the system does not shut down by selcting the shutdown option on the panel, anyway it restarted  back to the same position - the basic login prompt.

I ran startx again, and once again my pretty desktop came back - so its there just gotta make it persistent i guess.

Ran through 'sudo dpkg-reconfigure xserver-xorg'  upon rebooting it went into a routins disk check and said it detected and repaired errors on the boot partition...   and came back looking the same...

So i am installing fluxbox anyway... I need to go to bed... snore.

---

### Post by Matt Damon on 2009-03-27
So Fluxbox seemed to install OK, but still the same problem.  Good news though you got me to the point that I can manually get to my desktopm by logging in and running 'Startx'...   Close, but no cigar...     And there is the shutdown problem and the OAFIID:GNOME window...

I better get my beuty sleep - hard day on the film set tomorrow...

---

### Post by Matt Damon on 2009-03-27
Ran sudo-gnome session with the following results. 


pik@Pikachu:~$ sudo gnome-session
gnome-session[5402]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
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
gnome-session[5402]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
seahorse nautilus module initialized
Initializing nautilus-share extension
Shutting down nautilus-share extension
seahorse nautilus module shutdown

** (gnome-panel:5509): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)
gnome-session[5402]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
13
starting HAL detection for ac adaptors...
** (update-notifier:5557): WARNING **: not starting for system user


** (nm-applet:5548): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5548): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
none found
Throttle level is 0
alarm-notify.c:240 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1851 (alarm_queue_init)
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Mar 28 13:00:00 2009
 
evolution-alarm-notify-Message: Setting timeout for 8525 1238198400 1238189875
evolution-alarm-notify-Message:  Sat Mar 28 13:00:00 2009

evolution-alarm-notify-Message:  Sat Mar 28 10:37:55 2009

Disk space is low!

---

### Post by Matt Damon on 2009-03-27
So i reinstalled the desktop. 

root@Pikachu:/root# sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alsa-base alsa-utils fast-user-switch-applet gdm gdm-guest-session
  linux-sound-base
Suggested packages:
  alsa-oss xnest uswsusp gdm-themes
The following NEW packages will be installed:
  alsa-base alsa-utils fast-user-switch-applet gdm gdm-guest-session
  linux-sound-base ubuntu-desktop
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 3768kB of archives.
After this operation, 22.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main linux-sound-base 1.0.17.dfsg-2ubuntu1 [30.1kB]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main alsa-base 1.0.17.dfsg-2ubuntu1 [220kB]
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main alsa-utils 1.0.17-0ubuntu3 [1056kB]
Get:4 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main gdm 2.20.8-0ubuntu3 [1973kB]
Get:5 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main fast-user-switch-applet 2.24.0-0ubuntu6 [457kB]
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main gdm-guest-session 0.6.1 [5140B]
Get:7 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main ubuntu-desktop 1.124 [27.6kB] 
Fetched 3768kB in 8s (467kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package linux-sound-base.
(Reading database ... 115868 files and directories currently installed.)
Unpacking linux-sound-base (from .../linux-sound-base_1.0.17.dfsg-2ubuntu1_all.deb) ...
Selecting previously deselected package alsa-base.
Unpacking alsa-base (from .../alsa-base_1.0.17.dfsg-2ubuntu1_all.deb) ...
Selecting previously deselected package alsa-utils.
Unpacking alsa-utils (from .../alsa-utils_1.0.17-0ubuntu3_i386.deb) ...
Selecting previously deselected package gdm.
Unpacking gdm (from .../gdm_2.20.8-0ubuntu3_i386.deb) ...
Selecting previously deselected package fast-user-switch-applet.
Unpacking fast-user-switch-applet (from .../fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb) ...
Selecting previously deselected package gdm-guest-session.
Unpacking gdm-guest-session (from .../gdm-guest-session_0.6.1_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.124_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up linux-sound-base (1.0.17.dfsg-2ubuntu1) ...

Setting up alsa-base (1.0.17.dfsg-2ubuntu1) ...

Setting up alsa-utils (1.0.17-0ubuntu3) ...

Setting up gdm (2.20.8-0ubuntu3) ...
Adding group `gdm' (GID 113) ...
Done.
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 105) ...
Adding new user `gdm' (UID 105) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/gdm' does not belong to the user you are currently creating.
usermod: no changes
usermod: no changes
usermod: no changes
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Setting up fast-user-switch-applet (2.24.0-0ubuntu6) ...

Setting up gdm-guest-session (0.6.1) ...
Setting up ubuntu-desktop (1.124) ...
Processing triggers for menu ...
root@Pikachu:/root# sudo gnome-session
gnome-session[5963]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
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
gnome-session[5963]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
seahorse nautilus module initialized
Initializing nautilus-share extension
Shutting down nautilus-share extension
seahorse nautilus module shutdown
gnome-session[5963]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:6110): WARNING **: Tracker daemon is already running - attempting to run in readonly mode
Failure: Module initalization failed
starting HAL detection for ac adaptors...
** (update-notifier:6116): WARNING **: not starting for system user


** (nm-applet:6107): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6107): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
alarm-notify.c:240 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1851 (alarm_queue_init)
alarm-queue.c:219 (queue_midnight_refresh) - Refresh at Sat Mar 28 13:00:00 2009
 
evolution-alarm-notify-Message: Setting timeout for 7636 1238198400 1238190764
evolution-alarm-notify-Message:  Sat Mar 28 13:00:00 2009

evolution-alarm-notify-Message:  Sat Mar 28 10:52:44 2009

none found
Throttle level is 0
^CTraceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 352, in <module>
    waitloop.run()
KeyboardInterrupt
root@Pikachu:/root# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
The following packages will be REMOVED:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 52.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116328 files and directories currently installed.)
Removing linux-headers-2.6.27-7-generic ...
Removing linux-headers-2.6.27-7 ...
root@Pikachu:/root#

---

### Post by Matt Damon on 2009-03-27
Fixed.  SOlved.  Repaired.

So this is what I think may (or may not) have contributed fixed it.  

Thanks GeeZor for the inspiration.

sudo apt-get update
sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fluxbox
sudo apt-get install ubuntu-desktop

Windows is not as fun as this.

---

### Post by GeeZor on 2009-04-06
That is just great.

And you know what the best part is?
YOU HAD FUN!!!  :) :) :)

---

