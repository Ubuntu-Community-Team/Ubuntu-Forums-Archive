---
title: "Compiz makes me do alot of work"
date: 2008-07-14
forum: General Help
---

### Post by Deo Favente on 2008-07-14
Ever since i installed compiz, it makes me do alot of work for it. Here is the continual sequence i must follow:
1)Start computer
2)Splash screen
3)Screen flashes black
4)Login with normal session
5)Screen flashes black
6)Background color shows up along with curser controlled by me but otherwise blank screen
7)Screen flashes black
8)Repeat steps 6 & 7
9)Background images and menu bars show up and still curser controlled by me
10)screen flashes black
11)entire desktop shows, but is frozen (incorrect password error is supposed to show up from kopete but doesnt) and accepts no input from me
12)after awhile it unfreezes
13)NORMAL OPERATION (altho gfx is semi-slow) until SHUT DOWN
14)Reapeat steps 1-11 WTFH
15)After awhie screen flashes REALLY FAST to black screen with some text, cannot read but looks like some boot up stuff but nothing in all caps at least
16)Login with gnome safe mode
17)uninstall compiz
18)reinstall compiz
19)Shutdown
20)startup
21)Login with nomral session
22)Repeat steps 14 & 15
23)Reapeat steps 19 & 20
24)cycle repeats

If i do not follow this procedure, i can never reach normal operation. If i make it so that steps 22 and 23 never happens, my computer wont let me use any gui stuff until those two steps happen. If i never do step 18 and restart my computer i will ever reach steps 1-11 and then skipping 12 & 13 where gui doesnt work. My question is WTFH how do i get compiz to work correctly?:confused:](*,):frown:. Any ideas? Uh yea, latest ubuntu version, i dont know what else you need, just tell me what and how to find out.

EDIT: This isn't THAT big of a problem cause i use this computer as a personal/dev/server computer so cause of the servers step 13 lasts a few days or more. but its a big hassle when my computer freezes or update manager says it installed a new kernal or something and needs to reboot.

---

### Post by Deo Favente on 2008-07-14
LOL i think i might have accidentally stumbled upon something, ~/.xsessionerrors
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".

Fatal server error:
no GLX visuals available

rm: cannot remove `/tmp/.X1-lock': No such file or directory
rm: cannot remove `/tmp/.X11-unix/X1': No such file or directory
Waiting 9 more seconds for Xgl to start...
Waiting 8 more seconds for Xgl to start...
Waiting 7 more seconds for Xgl to start...
Waiting 6 more seconds for Xgl to start...
Waiting 5 more seconds for Xgl to start...
Waiting 4 more seconds for Xgl to start...
Waiting 3 more seconds for Xgl to start...
Waiting 2 more seconds for Xgl to start...
Waiting 1 more seconds for Xgl to start...
Waiting 0 more seconds for Xgl to start...
Xgl server failed to start!  Continuing without Xgl.
Desktop effects may be unavailable without Xgl
SESSION_MANAGER=local/Onyx:/tmp/.ICE-unix/7882
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
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
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

** (nautilus:8011): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8011): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:8011): WARNING **: Can not get _NET_WORKAREA

** (nautilus:8011): WARNING **: Can not determine workarea, guessing at layout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...

** (trackerd:8118): WARNING **: Tracker daemon is already running - attempting to run in readonly mode
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD
Throttle level is 0
11
evolution-alarm-notify-Message: Setting timeout for 86175 1216098000 1216011825
evolution-alarm-notify-Message:  Tue Jul 15 00:00:00 2008

evolution-alarm-notify-Message:  Mon Jul 14 00:03:45 2008

kbuildsycoca running...

** (nautilus:8011): WARNING **: Unable to add monitor: Not supported
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
VIDIOC_ENUM_FMT: Invalid argument
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: 
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[1216011823,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the applicationICE default IO error handler doing an exit(), pid = 7991, errno = 0
After reading this i opened up the terminal and keymashed some more but with no success. can any decode this file so that compiz works correctly?

---

### Post by Deo Favente on 2008-07-14
i made more success horray! When in failsafe gnome mode i looked in the tmp dir and found a .X0-lock instead of a .X1-lock. maybe if it needs to remove a lock is there a way i can get it to remove both files? please help me fix compiz!

---

### Post by mtbsoft on 2008-07-14
Don't take this the wrong way but, if this is a server box, shouldn't you be keeping it simple? Seems like the easiest way is to not use/install compiz - avoid the problem altogether.

---

### Post by Deo Favente on 2008-07-15
i said personal + dev + server, but only around 75% of each gets done as a compromise. Anyway i opened up the terminal and keymashed my keyboard until my hands flew off and somehow i fixed it. I changed something with the start up script and then it started working correctly. But onto the next problem: opengl only works 80% and is kinda slow.

---

### Post by phredbull on 2010-11-05
> **Deo Favente said:**
> Ever since i installed compiz, it makes me do alot of work for it. Here is the continual sequence i must follow:
1)Start computer
2)Splash screen
3)Screen flashes black
4)Login with normal session
5)Screen flashes black
6)Background color shows up along with curser controlled by me but otherwise blank screen
7)Screen flashes black
8)Repeat steps 6 & 7
9)Background images and menu bars show up and still curser controlled by me
10)screen flashes black
11)entire desktop shows, but is frozen (incorrect password error is supposed to show up from kopete but doesnt) and accepts no input from me
12)after awhile it unfreezes
13)NORMAL OPERATION (altho gfx is semi-slow) until SHUT DOWN
14)Reapeat steps 1-11 WTFH
15)After awhie screen flashes REALLY FAST to black screen with some text, cannot read but looks like some boot up stuff but nothing in all caps at least
16)Login with gnome safe mode
17)uninstall compiz
18)reinstall compiz
19)Shutdown
20)startup
21)Login with nomral session
22)Repeat steps 14 & 15
23)Reapeat steps 19 & 20
24)cycle repeats
Every time you turn your computer on? Do you have this process memorized, or do you use a cheat sheet? If I had to do this every time I wanted to use my computer, I'd definitely just use Windoze.

---

### Post by Elfy on 2010-11-05
Closed - 2 year old support thread.

---

