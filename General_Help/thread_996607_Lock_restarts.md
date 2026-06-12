---
title: "Lock restarts"
date: 2008-11-29
forum: General Help
---

### Post by fuzzybear3965 on 2008-11-29
Hey whenever I lock my PC for an extended time (I suppose an hour or more (I'm gone when it happens)) it restarts.  I know because I've asked my house and no one else has touched it and all my programs are off (Deluge, Firefox, etc.).  I've checked my power management settings and my screensaver settings.  Nothing is set to restart or power off after a certain amount of time.  The only setting is that the screensaver comes on after 5 minutes.  Then after (I don't know) 15-60 minutes later it restarts.  Again, never been there when it does (friggin' white whale).  PLEASE HELP!!!

---

### Post by fooey on 2008-11-29
Anything in your logs? 

check /var/log/messages  or syslog

---

### Post by fuzzybear3965 on 2008-11-29
Yeah, thanks for replying.  This is what I got in the action section of the log.  The rest is attached

```
Nov 28 15:05:48 john bonobo-activation-server (john-11664): could not associate with desktop session: Failed to connect to socket /tmp/dbus-dP9T7Cg4Qr: Connection refused
Nov 28 15:05:59 john pulseaudio[11746]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 28 15:05:59 john pulseaudio[11748]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 28 15:05:59 john pulseaudio[11748]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 28 15:05:59 john pulseaudio[11748]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Nov 28 15:33:25 john -- MARK --
Nov 28 15:53:25 john -- MARK --
Nov 28 16:13:25 john -- MARK --
Nov 28 16:33:25 john -- MARK --
Nov 28 16:53:25 john -- MARK --
Nov 28 17:13:25 john -- MARK --
Nov 28 17:33:25 john -- MARK --
Nov 28 17:53:25 john -- MARK --
Nov 28 18:13:25 john -- MARK --
Nov 28 18:33:25 john -- MARK --
Nov 28 18:53:25 john -- MARK --
Nov 28 19:13:25 john -- MARK --
Nov 28 19:33:25 john -- MARK --
Nov 28 19:53:25 john -- MARK --
Nov 28 20:13:25 john -- MARK --
Nov 28 20:33:25 john -- MARK --
Nov 28 20:53:25 john -- MARK --
Nov 28 21:13:25 john -- MARK --
Nov 28 21:22:58 john kernel: [44989.920056] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126 
Nov 28 21:22:58 john kernel: [44989.924036] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126 
Nov 28 21:22:58 john kernel: [44990.177968] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126 
Nov 28 21:22:58 john kernel: [44990.680030] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126 
Nov 28 21:22:59 john kernel: [44991.432033] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126 
Nov 28 21:23:00 john kernel: [44992.436037] Inbound IN=eth1 OUT= MAC= SRC=192.168.1.2 DST=239.192.152.143 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=6771 DPT=6771 LEN=126
```


The link to the messages file online:

[http://encodable.com/uploaddemo/files/John/messages](http://encodable.com/uploaddemo/files/John/messages)

---

