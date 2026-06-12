---
title: "latitude d630 amd64 8.04 blinking screen crashes ACPI related?"
date: 2009-06-29
forum: Hardware
---

### Post by misha680 on 2009-06-29
Dear All:

I have been having problems with my Dell Latitude d630 crashing under Ubuntu 8.04 amd64 for some time. I thought these issues were related to my NVIDIA card but have had them after uninstalling the NVIDIA proprietary drivers altogether and now think it is ACPI related.

The only line I could find in /var/log/syslog around the time of crashes 
consistently is:
```

Jun 28 22:08:27 misha-d630 kernel: [  514.941528] gnome-power-man[7400]: segfault at 0 rip 41141a rsp 7fffbd1f0260 error 4

```

Errors include a blinking screen and unresponsive computer. However I am usually able to turn it off safely by pressing the power button & waiting. I am now trying to boot with acpi=off and so far things seem okay.

The problems occured when:
1. Printing out of evolution using hplip (but not consistently).
2. On [www.bikeforums.org](www.bikeforums.org) (seemingly fairly consistently) using firefox.

Thank you
Misha

p.s. here's a fairly complete log when I had the NVIDIA proprietary drivers installed so you can see the weird NVRM messages as well. But again note this also occurs _without_ proprietary drivers. Thank you.

```

Jun 28 21:25:42 misha-d630 NXSERVER-3.3.0-22[6623]: User 'misha' logged in from '127.0.0.1'. 'NXLogin::set'
Jun 28 21:25:44 misha-d630 NXSERVER-3.3.0-22[6623]: Selected node host:localhost with port:22 'main::selectNode'
Jun 28 21:25:44 misha-d630 NXSERVER-3.3.0-22[6623]: Current selected node: localhost is in status: running  'main::selectNode'
Jun 28 21:25:44 misha-d630 NXSERVER-3.3.0-22[6623]: Selected session type: unix-gnome allowed in the profile of user: misha 'NXShell::Static'
Jun 28 21:25:49 misha-d630 NXSERVER-3.3.0-22[6623]: Session 'CAF9352E626CE0EE75C81CC75EFB3484' started by user 'misha'. 'NXShell::handler_session_start'
Jun 28 21:25:49 misha-d630 NXSERVER-3.3.0-22[6623]: User 'misha' from '127.0.0.1' logged out. 'NXLogin::reset'
Jun 28 21:25:49 misha-d630 NXNODE-3.3.0-17[6639]: Using port '1181' on node 'misha-d630' for session 'unix-gnome'. Logger::log nxnode 6132
Jun 28 21:25:49 misha-d630 NXNODE-3.3.0-17[6639]: Using host from available host list: 'localhost'. Logger::log nxnode 6133
Jun 28 21:25:53 misha-d630 pulseaudio[6697]: module-esound-sink.c: Connection failed: Connection refused
Jun 28 21:25:59 misha-d630 hcid[6028]: Default passkey agent (:1.26, /org/bluez/passkey) registered
Jun 28 21:26:00 misha-d630 hcid[6028]: Default authorization agent (:1.26, /org/bluez/auth) registered
Jun 28 21:26:10 misha-d630 kernel: [  107.163727] gnome-power-man[6826]: segfault at 0 rip 41141a rsp 7fff53044790 error 4
Jun 28 21:26:12 misha-d630 python: hp-systray[6722]: error: option -s not recognized
Jun 28 21:28:58 misha-d630 kernel: [  232.962839] Machine check events logged
Jun 28 21:29:48 misha-d630 kernel: [  265.538924] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:48 misha-d630 kernel: [  265.636047] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  265.728056] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  265.811358] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  265.894154] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  265.978566] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  266.063395] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:29:49 misha-d630 kernel: [  266.146739] NVRM: Xid (0001:00): 6, PE0001 
Jun 28 21:30:00 misha-d630 ddclient[5427]: FAILED:   updating misha-d630.dyndns.org: nohost: The hostname specified does not exist in the database
Jun 28 21:30:16 misha-d630 init: tty4 main process (4921) killed by TERM signal
Jun 28 21:30:16 misha-d630 init: tty5 main process (4922) killed by TERM signal
Jun 28 21:30:16 misha-d630 init: tty2 main process (4924) killed by TERM signal
Jun 28 21:30:16 misha-d630 init: tty3 main process (4926) killed by TERM signal
Jun 28 21:30:16 misha-d630 init: tty6 main process (4928) killed by TERM signal
Jun 28 21:30:16 misha-d630 init: tty1 main process (6395) killed by TERM signal
Jun 28 21:30:17 misha-d630 NXSERVER-3.3.0-22[6665]: ERROR: Ignoring message status 'Suspending' on session id: CAF9352E626CE0EE75C81CC75EFB3484 'NXShell::nxsessionSetStatus'
Jun 28 21:30:27 misha-d630 console-kit-daemon[5903]: WARNING: Unable to activate console: No such device or address 
Jun 28 21:30:27 misha-d630 avahi-daemon[5379]: Got SIGTERM, quitting.
Jun 28 21:30:27 misha-d630 avahi-daemon[5379]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.50.
Jun 28 21:30:28 misha-d630 xinetd[5855]: Exiting...
Jun 28 21:30:31 misha-d630 exiting on signal 15
Jun 28 21:47:12 misha-d630 syslogd 1.5.0#1ubuntu1: restart.

```

---

### Post by jaymcd on 2009-11-04
Mine crashes all the time too. I am pretty sure it relates to the video as it seems to crash when I run videos or run dual monitors - put the card under stress. I am running VMware on it as well.

Question - why are you running the amd64 kernel ?

---

### Post by misha680 on 2009-11-04
> **jaymcd said:**
> Mine crashes all the time too. I am pretty sure it relates to the video as it seems to crash when I run videos or run dual monitors - put the card under stress. I am running VMware on it as well.

Question - why are you running the amd64 kernel ?

Mine was hardware issue... Dell swapped out mobo and fixed it.

amd64... you can access >3gb of RAM.

Misha

---

### Post by jaymcd on 2009-11-04
OK. No other issues with this kernel? i.e. Is it not tuned for AMD or ?

---

### Post by jaymcd on 2009-11-04
PS

I had my motherboard replaced previously as it was crashing in XP - giving all kinds of GPU errors.

---

