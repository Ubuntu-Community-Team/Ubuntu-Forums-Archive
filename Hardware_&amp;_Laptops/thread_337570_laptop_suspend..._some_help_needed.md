---
title: "laptop suspend... some help needed"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by Choad on 2007-01-13
im trying to make suspend work. i really need this feature!

at one point, it would suspend but not resume (it would just go to a blueish screen) but now it doesnt even suspend

```

Jan 13 13:07:37 richard-laptop gnome-power-manager: (richard) Suspending computer because the DBUS method Suspend() was invoked
Jan 13 13:07:39 richard-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 3305
Jan 13 13:07:40 richard-laptop dhclient: removed stale PID file
Jan 13 13:07:40 richard-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jan 13 13:07:40 richard-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jan 13 13:07:40 richard-laptop dhclient: All rights reserved.
Jan 13 13:07:40 richard-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 13 13:07:40 richard-laptop dhclient: 
Jan 13 13:07:40 richard-laptop dhclient: Listening on LPF/eth0/00:a0:d1:c1:ab:2c
Jan 13 13:07:40 richard-laptop dhclient: Sending on   LPF/eth0/00:a0:d1:c1:ab:2c
Jan 13 13:07:40 richard-laptop dhclient: Sending on   Socket/fallback
Jan 13 13:08:44 richard-laptop syslogd 1.4.1#18ubuntu6: restart.

```
and after this point there is an assload of logs from the boot-sequence.

if i understand this right... it is something to do with my network thats causing it to mess up. but why when i suspend it would it want to look for a network connection? and eth0 was already connected when i invoked the suspend 

*confused*

i really, REALLY need this to be fixed, so please can you good people help me out. anything you want me to test out just say

the laptop is a very rare make: a zepto "Znote 6214W", but i got it specifically because it looked to have excellent linux compatibility. (intel wireless, nvidia graphics etc.) and indeed everything does work, and even hibernate works, but hibernate is about the same speed as a cold boot so its useless.

anyway thanks in advance for any help

---

### Post by Choad on 2007-01-13
bumpy bump

---

### Post by Choad on 2007-01-13
bump

---

### Post by Choad on 2007-01-14
ok i got it to suspend again. random eh?


this is from when it was waking up. there are a LOT of logs before this, but this is the bit that gets interesting. all the logs previous to this have the time stamp 14 11:27:18, which means it has been instentanious up until this point.
```
Jan 14 11:27:18 richard-laptop kernel: [17179597.096000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 14 11:27:20 richard-laptop hpiod: 1.6.9 accepting connections at 2208... 
Jan 14 11:27:20 richard-laptop kernel: [17179600.296000] eth0: no IPv6 routers present
**Jan 14 11:27:21 richard-laptop kernel: [17179600.756000] apm: BIOS not found.**
Jan 14 11:27:29 richard-laptop kernel: [17179609.208000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jan 14 11:27:30 richard-laptop kernel: [17179609.324000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 14 11:27:30 richard-laptop kernel: [17179609.328000] NFSD: starting 90-second grace period
Jan 14 11:27:31 richard-laptop rpc.statd[4618]: Version 1.0.9 Starting
Jan 14 11:27:31 richard-laptop hcid[4634]: Bluetooth HCI daemon
Jan 14 11:27:31 richard-laptop hcid[4634]: Register path:/org/bluez fallback:1
Jan 14 11:27:31 richard-laptop hcid[4634]: HCI dev 0 registered
Jan 14 11:27:31 richard-laptop hcid[4634]: Register path:/org/bluez/hci0 fallback:0
Jan 14 11:27:31 richard-laptop kernel: [17179610.480000] Bluetooth: L2CAP ver 2.8
Jan 14 11:27:31 richard-laptop kernel: [17179610.480000] Bluetooth: L2CAP socket layer initialized
Jan 14 11:27:31 richard-laptop sdpd[4638]: Bluetooth SDP daemon 
Jan 14 11:27:31 richard-laptop hcid[4634]: HCI dev 0 up
Jan 14 11:27:31 richard-laptop hcid[4634]: Device hci0 has been added
Jan 14 11:27:31 richard-laptop hcid[4634]: Starting security manager 0
Jan 14 11:27:31 richard-laptop kernel: [17179610.488000] Bluetooth: RFCOMM socket layer initialized
Jan 14 11:27:31 richard-laptop kernel: [17179610.488000] Bluetooth: RFCOMM TTY layer initialized
Jan 14 11:27:31 richard-laptop kernel: [17179610.488000] Bluetooth: RFCOMM ver 1.7
Jan 14 11:27:31 richard-laptop hcid[4634]: Device hci0 has been activated
Jan 14 11:27:31 richard-laptop hcid[4634]: return_link_keys (sba=00:0D:F0:2E:5C:A6, dba=00:04:61:80:DB:D9)
Jan 14 11:27:31 richard-laptop anacron[4671]: Anacron 2.3 started on 2007-01-14
Jan 14 11:27:31 richard-laptop anacron[4671]: Will run job `cron.daily' in 5 min.
Jan 14 11:27:31 richard-laptop anacron[4671]: Jobs will be executed sequentially
Jan 14 11:27:31 richard-laptop /usr/sbin/cron[4697]: (CRON) INFO (pidfile fd = 3)
Jan 14 11:27:31 richard-laptop /usr/sbin/cron[4698]: (CRON) STARTUP (fork ok)
[B]Jan 14 11:27:31 richard-laptop /usr/sbin/cron[4698]: (CRON) INFO (Running @reboot jobs)
Jan 14 11:27:41 richard-laptop hcid[4648]: Can't set scan mode on hci0: Connection timed out (110)[/B]
Jan 14 11:32:31 richard-laptop anacron[4671]: Job `cron.daily' started
[B]Jan 14 11:32:31 richard-laptop anacron[4797]: Updated timestamp for job `cron.daily' to 2007-01-14
Jan 14 11:32:48 richard-laptop gdmgreeter[4451]: Theme broken: must have pam-message label![/B]
Jan 14 11:32:53 richard-laptop gconfd (richard-5027): starting (version 2.16.0), pid 5027 user 'richard'
Jan 14 11:32:53 richard-laptop gconfd (richard-5027): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 14 11:32:53 richard-laptop gconfd (richard-5027): Resolved address "xml:readwrite:/home/richard/.gconf" to a writable configuration source at position 1
Jan 14 11:32:53 richard-laptop gconfd (richard-5027): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 14 11:32:53 richard-laptop gconfd (richard-5027): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
[B]Jan 14 11:32:53 richard-laptop gconfd (richard-5027): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 14 11:33:00 richard-laptop gconfd (richard-5027): Resolved address "xml:readwrite:/home/richard/.gconf" to a writable configuration source at position 0
Jan 14 11:33:35 richard-laptop exiting on signal 15
[/B]
```

lots of those ones in bold.... they were taking a very long time!

to be honest, 11:32:18 to 11:32:35.... thats over a minute. i didnt wait that long. which confuses me!. i waited.... 30 seconds tops.

does ANYONE have any idea?

---

### Post by Choad on 2007-01-14
well, the response was overwhelming.... lol. fixed it with suspend2 patched kernel

very, very worth checking out if you have suspend problems

[http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/)

---

