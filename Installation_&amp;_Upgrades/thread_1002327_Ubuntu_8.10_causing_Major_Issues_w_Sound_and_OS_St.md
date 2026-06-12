---
title: "Ubuntu 8.10 causing Major Issues w/ Sound and OS Stability"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by DDurcsak on 2008-12-04
To any and all:

Loaded 8.10 shortly after it came out. OS specs:
UBUNTU: 2.6.27-7 / 8.10
and system started to act up almost right away.

I had started with Ubuntu 8.04 and everything worked fine..system screamed.

Problem was first noted when playing video on Firefox (3.0.4) and there was no sound. I checked Sound Preferences and when I ran test the following msg came up:

audiotestsrc wave=sine freq=512!
audioconvert ! audiosample ! gconfaudiosink:
Failed to connect stream; invalid argument

Can not close out error box.

Another issue is that some applications will hang and system has to be hard rebooted.

I then went to the User.Log and found this for each day after I loaded 8.10 Ubuntu:

User.log

Nov 30 14:51:23 david-desktop bonobo-activation-server (david-8491): could not associate with desktop session: Failed to connect to socket /tmp/dbus-DUG18Hzx13: Connection refused
Nov 30 14:51:28 david-desktop bonobo-activation-server (david-8685): could not associate with desktop session: Failed to connect to socket /tmp/dbus-DUG18Hzx13: Connection refused
Nov 30 17:09:27 david-desktop pulseaudio[7134]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 30 17:09:27 david-desktop pulseaudio[7136]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 30 17:09:27 david-desktop pulseaudio[7136]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 30 17:09:27 david-desktop pulseaudio[7136]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Nov 30 17:09:27 david-desktop pulseaudio[7136]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_a lsa_playback_0"): initialization failed.
Nov 30 17:09:51 david-desktop pulseaudio[7136]: module-x11-xsmp.c: X11 session manager not running.
Nov 30 17:09:51 david-desktop pulseaudio[7136]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 30 17:13:33 david-desktop compiz.real: *** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0928a8d8 ***
Nov 30 17:13:38 david-desktop bonobo-activation-server (david-7933): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HYMu1aOJFo: Connection refused
Dec 1 22:58:55 david-desktop pulseaudio[6035]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 1 22:58:55 david-desktop pulseaudio[6037]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 1 22:58:55 david-desktop pulseaudio[6037]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 1 22:58:55 david-desktop pulseaudio[6037]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec 1 22:58:55 david-desktop pulseaudio[6037]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_a lsa_playback_0"): initialization failed.
Dec 1 22:59:19 david-desktop pulseaudio[6037]: module-x11-xsmp.c: X11 session manager not running.
Dec 1 22:59:19 david-desktop pulseaudio[6037]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Dec 2 08:14:07 david-desktop bonobo-activation-server (david-14473): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ZHvbRq2Nya: Connection refused
Dec 2 08:31:33 david-desktop pulseaudio[6448]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 2 08:31:33 david-desktop pulseaudio[6450]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 2 08:31:33 david-desktop pulseaudio[6450]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 2 08:31:33 david-desktop pulseaudio[6450]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec 2 08:31:33 david-desktop pulseaudio[6450]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_a lsa_playback_0"): initialization failed.
Dec 2 08:31:57 david-desktop pulseaudio[6450]: module-x11-xsmp.c: X11 session manager not running.
Dec 2 08:31:57 david-desktop pulseaudio[6450]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.
Dec 3 22:50:52 david-desktop compiz.real: *** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x08250e30 ***
Dec 3 22:50:52 david-desktop bonobo-activation-server (david-4266): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LoSSiRcl5I: Connection refused
Dec 3 22:50:57 david-desktop bonobo-activation-server (david-4513): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LoSSiRcl5I: Connection refused
Dec 3 22:52:52 david-desktop pulseaudio[6137]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 3 22:52:52 david-desktop pulseaudio[6139]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 3 22:52:52 david-desktop pulseaudio[6139]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 3 22:52:52 david-desktop pulseaudio[6139]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Dec 3 22:52:52 david-desktop pulseaudio[6139]: module.c: Failed to load module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_a lsa_playback_0"): initialization failed.
Dec 3 22:53:16 david-desktop pulseaudio[6139]: module-x11-xsmp.c: X11 session manager not running.
Dec 3 22:53:16 david-desktop pulseaudio[6139]: module.c: Failed to load module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by salubrium on 2008-12-05
I have pretty much the same issue

Playing AssaultCube, sometimes it locks and Ctrl+Alt+Backspace is only way out. When I log back in, everything is extremely slow ie: Alt+F2 can take 10 seconds to bring up run dialogue but iotop, top etc show no load, no major activity. Hard drive is mostly idle.

Then AssaultCube won't reload, Flash won't work, freezing the browser for 20 seconds if I try and hit and flash site that uses sound.


Restarting alsa or pulseaudio doesn't fix it and the only thing that corrects it is to reboot the machine. It's only been an issue since stable release of 8.10. I don't remember this happening earlier and I have been on Ibex since late Alpha.

Here's a sample of user.log

Dec  6 12:04:19 srv1 bonobo-activation-server (user-23908): could not associate with desktop session: Failed to connect to socket /tmp/dbus-G4iHNntaFu: Connection refused
Dec  6 12:06:58 srv1 libvirtd: Shutting down on signal 15
Dec  6 12:09:31 srv1 ntop[8374]:   THREADMGMT[t139694950008544]: ntop RUNSTATE: PREINIT(1)
Dec  6 12:09:31 srv1 ntop[8374]:   THREADMGMT[t139694950008544]: ntop RUNSTATE: INIT(2)
Dec  6 12:09:40 srv1 dhcdbd: Started up.
Dec  6 12:09:48 srv1 ltsp: No client chroots found, please run ltsp-build-client
Dec  6 12:09:49 srv1 ltsp: No client chroots found, please run ltsp-build-client
Dec  6 12:10:41 srv1 pulseaudio[11111]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  6 12:10:41 srv1 pulseaudio[11113]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  6 12:10:41 srv1 pulseaudio[11113]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted


There's certainly a bug somewhere relating to the audio but I can't easily replicate it to do a trace

---

### Post by linksys101 on 2008-12-30
I'm going down to 8.04, 8.10 seemed to unstable for now.

---

