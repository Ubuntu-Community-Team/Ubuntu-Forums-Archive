---
title: "X windows crashes"
date: 2008-08-20
forum: General Help
---

### Post by goodtimes200 on 2008-08-20
I am running 8.04 on an AMD 64 bit machine with compiz-fusion. I am getting more and more X-window session crashes that take me back to the login screen. The only problem I am seeing is /var/log/messages:


Aug 20 20:01:04 glacier pulseaudio[13409]: pid.c: Stale PID file, overwriting.
Aug 20 20:01:04 glacier pulseaudio[13409]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 20 20:01:05 glacier pulseaudio[13409]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.

Any ideas? Thanks.

Edit: The crashes usually occur when I am dealing with Firefox.

---

### Post by goodtimes200 on 2008-08-20
Any suggestions other then changing the default-sample-rate to 48000 in my /etc/pulse/daemon.conf file? Any repercussions to this?

---

