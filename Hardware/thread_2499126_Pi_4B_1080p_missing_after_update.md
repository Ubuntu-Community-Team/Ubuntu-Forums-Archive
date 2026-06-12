---
title: "Pi 4B 1080p missing after update"
date: 2024-07-13
forum: Hardware
---

### Post by l-valerimanera on 2024-07-13
Just installed 24 desktop onto a 128GB SD and initial install was going fine.

Ran updates, and the maximum resolution is 1024x768.

1080p was working perfectly before updates & reboot.

This is a monitor via HDMI-0. I see the same behaviour on RPIOS.

---

### Post by TheFu on 2024-07-14
My pi4 runs:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 11 (bullseye)
Release:        11
Codename:       bullseye

$ uptime
 09:24:01 up 8 days, 19:49,  1 user,  load average: 0.84, 0.85, 0.83
```

Very stable.  
It was patched yesterday and 1080p on bcm2711-hdmi0 is working fine.  Don't know what to say.  Maybe try a different HDMI cable?  I'm using 8K capable BlueRigger cables. Further, since my pi4 is a media server, the HDMI cable is 25ft long to reach the family projector.

I'll reboot it now and see if that changes anything.  I have system backups, grabbed either daily or weekly (I don't recall).  Ok, rebooted.  
```
$ uptime
 09:25:55 up 0 min,  1 user,  load average: 2.53, 0.66, 0.22
```

Let me go and turn on the audio-visual system now and check the resolution.  1920x1080p. Looks nice.  Sorry, this doesn't help you much. The kernel is this:

```
$ uname -a
Linux pi4 5.15.92-1-osmc #1 SMP PREEMPT Tue Jul 25 00:03:42 UTC 2023 aarch64 GNU/Linux

```

Anyway, some local troubleshooting would be advised.

---

### Post by l-valerimanera on 2024-07-14
I have RaspiOS Bookworm on another SD card and it shows the exact same behaviour as Ubuntu 24.

1080p until I do updates, then locked to 1024x768.

---

### Post by TheFu on 2024-07-14
Welcome to the bleeding edge.  Can you run a 5.x kernel on those?
When I tried the 6.x kernels on my Ryzen, about 67% were unstable.  I decided that 6.x kernels weren't ready for my use.  Maybe in 2025.

---

