---
title: "No sound after upgrade from 8.10 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by emanuel75 on 2009-04-24
Hello,

I have upgraded from 8.10 to 9.04 today and have a problem now: Sound isn't working anymore (both in Gnome and KDE). Changing the audio settings doesn't have any effect.

I am using an Asus P5QL Pro motherboard, sound is on board. Who can help ...?

Thanks a lot!

---

### Post by mousestalker on 2009-04-24
> **emanuel75 said:**
> Hello,

I have upgraded from 8.10 to 9.04 today and have a problem now: Sound isn't working anymore (both in Gnome and KDE). Changing the audio settings doesn't have any effect.

I am using an Asus P5QL Pro motherboard, sound is on board. Who can help ...?

Thanks a lot!

Did you look here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ?
That might help isolate where the problem is.

---

### Post by Fuertes::Benjami on 2009-04-24
Hi. Had the same problem. It's been solved by following the instruccions on [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

except that libao-pulse wasn't found, but tried the suggestion of libao2... and volia!

 $ sudo apt-get install libasound2-plugins padevchooser libao2 libsdl1.2debian-pulseaudio

---

### Post by Fuertes::Benjami on 2009-04-24
voila! :-)

---

### Post by sb360 on 2009-04-24
Im having a similiar problem but even after following that guidline I get nothing. I keep getting an error from pulseaudio saying "Connection Failed: Connection Terminated"
It seems to have been installed but I cant get any sound out of my computer.

I have just installed 9.04 (reinstall rather than upgrade)

---

### Post by emanuel75 on 2009-04-24
Thank you all very much! Pulseaudio brought sound back to my computer! The volume seems to be a bit lower than before but it works now.

To sb360: In my case using Benjamin's command line

$ sudo apt-get install libasound2-plugins padevchooser libao2 libsdl1.2debian-pulseaudio

made the big difference. (Note that it 's different from the command line shown on [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) Maybe it helps you run your sound card too.

Thanks again!

---

### Post by jbraswell on 2009-04-25
I'm still having trouble.  When I try to run 

```
pulseaudio & pavucontrol
```

I get this

```
[1] 7493
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Xlib:  extension "RANDR" missing on display ":0.0".
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:7494): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(pavucontrol:7494): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio

```

---

### Post by sb360 on 2009-04-25
> **emanuel75 said:**
> Thank you all very much! Pulseaudio brought sound back to my computer! The volume seems to be a bit lower than before but it works now.

To sb360: In my case using Benjamin's command line

$ sudo apt-get install libasound2-plugins padevchooser libao2 libsdl1.2debian-pulseaudio

made the big difference. (Note that it 's different from the command line shown on [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) Maybe it helps you run your sound card too.

Thanks again!

Nope I did that and it seemed to complete fine but still no sound.

When I enter pulseaudio & pavucontrol I get this

[1] 27112
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[1]+  Exit 1                  pulseaudio

Then the control panel opens for a few seconds and then dies with the connection failed: connection terminated message again

---

### Post by jbraswell on 2009-04-26
> **sb360 said:**
> Nope I did that and it seemed to complete fine but still no sound.

When I enter pulseaudio & pavucontrol I get this

[1] 27112
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
[1]+  Exit 1                  pulseaudio

Then the control panel opens for a few seconds and then dies with the connection failed: connection terminated message again

I have no idea why, but I ran this

```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

just to get info on pulse audio, and afterwards, everything worked. (Yes, I had restarted multiple times before.)  Actually, after I did that, I had sound, but it was very quiet.  I had to run alsamixer and turn everything back up.  

Weird, weird Ubuntu.

---

### Post by cathalcummins on 2009-08-19
I am tempted to upgrade to Ubuntu Studio 9.04.

I recall that it took ages to tweak the sound on the initial setup; I'm running M-Audio Delta 44. Jack was a pain to get right too.

Is there any way I can get a snapshot image of my audio/video etc settings, like a backed up registry? That is, so I could just tell my system to search said folder and assign the settings as before.

Also, on a more practical note; is it worth upgrading at all (other than the eventual lack of support for v8.10)?

Thanks.

---

### Post by cathalcummins on 2009-08-26
I hope you don't mind me bumping this thread. :confused:

---

