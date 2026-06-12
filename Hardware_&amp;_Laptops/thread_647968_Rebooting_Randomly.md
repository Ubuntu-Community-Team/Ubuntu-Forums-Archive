---
title: "Rebooting Randomly"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by Socratez on 2007-12-23
Ok so I have an old laptop and I am still holding onto it (I'm cheap) and trying to make it work as my day to day PC. Lately I am unable to do anything except surf and IM because if i do anymore it shuts itself down. Now I read some logs and see that it has something to do with overheating but when I feel the exhaust air it doesn't seem overly warm at all. I started ahving this issue after upgrading to 7.10 in Nov. I reinstalled from scrath as well but still no luck. I want to get to the bottom of this because I miss my music. I don't have anything blocking the exhaust, I can't find a CPU Temp monitor tool either so I am not sure how to handle this.

It is a PIII 1.1GHz Toshiba Satellite 1800 ... ALi Chipset, Trident CyberBlade Video, 384MB Ram, 30GB HD, CD-RW Combo Drive D-Link PCMCIA Wireless card (Atheos).... If that helps ...

---

### Post by Socratez on 2007-12-23
I wanted to include some log file info just incase this is an issue with software. I see 68 degrees but I hardly call that over heating but I could be wrong. Pentium III 1.1GHz wouldn't opperate much lower then 50 I would think especially in a laptop. Could it be ACPI?


LOG INFO

[Kern.log]
Dec 23 10:20:41 csh-laptop kernel: [ 6530.960000] ACPI: Critical trip point
Dec 23 10:20:41 csh-laptop kernel: [ 6530.960000] Critical temperature reached (76 C), shutting down.
Dec 23 10:20:41 csh-laptop kernel: [ 6531.468000] Critical temperature reached (68 C), shutting down.
Dec 23 10:20:54 csh-laptop kernel: [ 6544.296000] ACPI: Critical trip point
Dec 23 10:20:54 csh-laptop kernel: [ 6544.296000] Critical temperature reached (76 C), shutting down.
Dec 23 10:20:54 csh-laptop kernel: [ 6544.864000] Critical temperature reached (68 C), shutting down.

[Messages]
Dec 23 10:20:41 csh-laptop kernel: [ 6530.960000] ACPI: Critical trip point
Dec 23 10:20:54 csh-laptop kernel: [ 6544.296000] ACPI: Critical trip point
Dec 23 10:21:04 csh-laptop exiting on signal 15
Dec 23 10:22:13 csh-laptop syslogd 1.4.1#21ubuntu3: restart.

[Daemon.log]
Dec 23 10:20:41 csh-laptop init: tty4 main process (4079) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty5 main process (4080) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty2 main process (4082) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty3 main process (4083) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty1 main process (4084) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty6 main process (4085) killed by TERM signal
Dec 23 10:20:58 csh-laptop avahi-daemon[4814]: Got SIGTERM, quitting.
Dec 23 10:20:58 csh-laptop avahi-daemon[4814]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.25
1.

[syslog]
Dec 23 10:17:02 csh-laptop /USR/SBIN/CRON[7908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 10:20:41 csh-laptop kernel: [ 6530.960000] ACPI: Critical trip point
Dec 23 10:20:41 csh-laptop kernel: [ 6530.960000] Critical temperature reached (76 C), shutting down.
Dec 23 10:20:41 csh-laptop init: tty4 main process (4079) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty5 main process (4080) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty2 main process (4082) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty3 main process (4083) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty1 main process (4084) killed by TERM signal
Dec 23 10:20:41 csh-laptop init: tty6 main process (4085) killed by TERM signal
Dec 23 10:20:41 csh-laptop kernel: [ 6531.468000] Critical temperature reached (68 C), shutting down.
Dec 23 10:20:54 csh-laptop kernel: [ 6544.296000] ACPI: Critical trip point
Dec 23 10:20:54 csh-laptop kernel: [ 6544.296000] Critical temperature reached (76 C), shutting down.
Dec 23 10:20:54 csh-laptop kernel: [ 6544.864000] Critical temperature reached (68 C), shutting down.
Dec 23 10:20:58 csh-laptop avahi-daemon[4814]: Got SIGTERM, quitting.
Dec 23 10:20:58 csh-laptop avahi-daemon[4814]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.25
1.
Dec 23 10:21:04 csh-laptop exiting on signal 15

---

