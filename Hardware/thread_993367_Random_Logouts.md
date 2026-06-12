---
title: "Random Logouts"
date: 2008-11-25
forum: Hardware
---

### Post by zerubbabel on 2008-11-25
I am running a clean install of Intrepid on a Dell Latitude d830 with the Intel gm965 express chipset. Hardy ran just fine on this hardware, and I'm nearly ready to go back to it because of only one very annoying problem: random logouts. The session logs itself out unexpectedly, with no apparent rhyme or reason. Sometimes the system is idle, sometimes I'm in the middle of doing something, but no clear pattern. The interval could be minutes to hours. 

Please, can someone help me? I really don't want to reinstall Hardy if I can help it...

---

### Post by zerubbabel on 2008-11-26
Here's the relevant section from /var/log/syslog, which seems to be a consistent pattern after each forced logout...

Nov 26 11:50:31 dz bluetoothd[5878]: link_key_request (sba=00:1E:37:AD:FC:67, dba=00:16:38:C7:83:9F)
Nov 26 11:50:31 dz kernel: [74709.588074] input: Think Outside Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/bluetooth/hci0/hci0:46/input41
Nov 26 11:50:32 dz gdm[15339]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov 26 11:50:34 dz acpid: client connected from 16704[0:0] 
Nov 26 11:50:40 dz gdmgreeter[16734]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Nov 26 11:50:47 dz pulseaudio[16844]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 26 11:50:47 dz pulseaudio[16846]: pid.c: Stale PID file, overwriting.
Nov 26 11:50:47 dz pulseaudio[16846]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 26 11:50:47 dz pulseaudio[16846]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 26 11:50:48 dz x-session-manager[16759]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov 26 11:50:58 dz x-session-manager[16759]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov 26 11:51:06 dz kernel: [74744.469567] canberra-gtk-pl[16972]: segfault at 49d42240 ip b711384d sp b6eacf10 error 6 in libpulse.so.0.4.1[b70d4000+4e000]
Nov 26 11:51:08 dz x-session-manager[16759]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Nov 26 11:51:08 dz pulseaudio[16846]: module-x11-xsmp.c: X11 session manager not running.
Nov 26 11:51:08 dz pulseaudio[16846]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by starcannon on 2008-11-26
just looking at your errors, I might try going into:
System>Preferences>Sound 
and setting everything to Alsa or OSS and see if it stops; to my eyes it looks like a Pulse Audio issue. I would recommend 8.04 anyway, I have some issues with 8.10 that are not present in 8.04; and indeed I only run 8.10 on a few laptops that the benefits outwieghed the problems on.

GL and have fun.

---

### Post by zerubbabel on 2008-11-26
Thanks for the suggestion, but I already have all my sound settings set to Alsa in System>Preferences>Sound, which makes me wonder why the Pulse Audio lines... But at any rate, how could that be the cause of the problem when those lines only show up *after* the fatal error and the X server restarts?

---

### Post by zerubbabel on 2008-11-28
bump...

---

### Post by zerubbabel on 2008-12-03
Well, for what it's worth, I seem to have bypassed the problem by switching to a corded keyboard and mouse instead of the Bluetooth keyboard and mouse I was using.

---

### Post by Hatchetfish on 2009-03-05
I have a very similar issue more directly traceable to a bluetooth keyboard*. 

The keyboard evidently powersaves, and has to reestablish a connection with the computer when I type something after a period of inactivity, and every so often (3 to 4 times a week) the result of trying to type when the keyboard is powersaved is 1) the keyboard attempts to reconnect, 2) I'm logged out of gnome with no confirmation, 3) I swear about any unsaved and now lost work.

*A Filco, so Japanese and not made for export, and as I don't speak or read Japanese, therefore effectively devoid of instructions.  I'm actually just assuming that the apparent disconnects after some idle period are powersaving, they could be something else.  Knock on wood they don't happen except when I've not pushed a key in a several minutes, so a reasonable assumption, but still observational assumption.  I only managed to connect it by drawing on ancient simian exploratory instincts...  Thankfully the stick and termites were not required.

---

