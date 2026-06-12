---
title: "Backup command issue"
date: 2011-09-21
forum: Hardware
---

### Post by ccilleperuma on 2011-09-21
Hello,

This not the Ubuntu but I came here also searching for a solution as its also a Linux distribution.

when I try to confirm the tape backup (LTO 4) it gives an error.
```
sapprdsvr:~ # mt -f /dev/st0 rewind
sapprdsvr:~ # tar -cfz /dev/st0 /tape_test/
tar: Removing leading `/' from member names
sapprdsvr:~ # mt -f /dev/st0 status
drive type = Generic SCSI-2 tape
drive status = 1174405120
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 0 bytes. Density code 0x46 (unknown).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN
sapprdsvr:~ # mt -f /dev/st0 tell
mt: /dev/st0: Input/output error
sapprdsvr:~ # mt -f /dev/st0 rewind
sapprdsvr:~ # mt -f /dev/st0 status
drive type = Generic SCSI-2 tape
drive status = 1174405120
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 0 bytes. Density code 0x46 (unknown).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN
sapprdsvr:~ # mt -f /dev/st0 tell
mt: /dev/st0: Input/output error
sapprdsvr:~ # tar -tzf /dev/st0
tar (child): /dev/st0: Cannot read: Input/output error
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
sapprdsvr:~ # cd /
sapprdsvr:/ # tar -xzf /dev/st0 tape_test/
tar (child): /dev/st0: Cannot read: Input/output error
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```


Is this because of mismatch block size? If so, How to overcome?
Else, please guide me to troubleshoot it..

Adding system log for more details..

```
Sep 21 09:27:28 sapprdsvr sshd[18114]: Accepted keyboard-interactive/pam for root from 192.168.51.75 port 49470 ssh2
Sep 21 09:27:47 sapprdsvr kernel: [835191.723871] st0: Sense Key : Illegal Request [current] 
Sep 21 09:27:47 sapprdsvr kernel: [835191.723886] st0: Add. Sense: Invalid field in cdb
Sep 21 09:30:01 sapprdsvr /usr/sbin/cron[18152]: (root) CMD ([ -x /usr/lib64/sa/sa1 ] && exec /usr/lib64/sa/sa1 -S ALL 1 1)
Sep 21 09:31:44 sapprdsvr kernel: [835429.015562] st0: Sense Key : Illegal Request [current] 
Sep 21 09:31:44 sapprdsvr kernel: [835429.015577] st0: Add. Sense: Invalid field in cdb
Sep 21 09:32:03 sapprdsvr kernel: [835448.319419] st0: Sense Key : Illegal Request [current] 
Sep 21 09:32:03 sapprdsvr kernel: [835448.319433] st0: Add. Sense: Invalid field in cdb
Sep 21 09:40:01 sapprdsvr /usr/sbin/cron[18195]: (root) CMD ([ -x /usr/lib64/sa/sa1 ] && exec /usr/lib64/sa/sa1 -S ALL 1 1)
Sep 21 09:40:33 sapprdsvr gnome-session[18224]: WARNING: GSIdleMonitor: IDLETIME counter not found
Sep 21 09:40:33 sapprdsvr gnome-session[18224]: WARNING: Owner of /tmp/orbit-gdm is not the current user
Sep 21 09:40:34 sapprdsvr pulseaudio[18252]: module.c: module-hal-detect is deprecated: Please use module-udev-detect instead of module-hal-detect!
Sep 21 09:40:34 sapprdsvr gdm-simple-greeter[18247]: GLib-GObject-CRITICAL: g_param_spec_flags: assertion `G_TYPE_IS_FLAGS (flags_type)' failed
Sep 21 09:40:34 sapprdsvr gdm-simple-greeter[18247]: GLib-GObject-CRITICAL: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Sep 21 09:40:38 sapprdsvr gdm-session-worker[18248]: WARNING: gdm_session_settings_load: lang = (null)
Sep 21 09:40:42 sapprdsvr gnome-session[18260]: WARNING: GSIdleMonitor: IDLETIME counter not found
Sep 21 09:40:43 sapprdsvr gnome-keyring-daemon[18349]: adding removable location: volume_label_Feb_2011_LTO_GM at /media/Feb_2011_LTO_GM_
Sep 21 09:40:43 sapprdsvr pulseaudio[18412]: pid.c: Stale PID file, overwriting.
Sep 21 09:40:43 sapprdsvr pulseaudio[18412]: module.c: module-hal-detect is deprecated: Please use module-udev-detect instead of module-hal-detect!
```


please help me to troubleshoot this issue.

Thanks.

C. C. Illeperuma

---

