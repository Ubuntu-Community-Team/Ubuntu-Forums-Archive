---
title: "Synce USB Not connecting"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by pschella on 2007-03-28
Hello Everyone,

I have a Compaq Ipaq (Pocket PC) that I would like to synchronize with my laptop (running Kubuntu Feisty Fawn). When I connect it to my laptop lsusb gives me

Bus 002 Device 004: ID 049f:0003 Compaq Computer Corp. iPAQ PocketPC

I installed synce-dccm, syncekonnector, synce-serial and all dependencies (via apt). When I start synce with the command synce-serial-start. My pocket pc displays "connectyng to host" but then retry apears 4 times and the connection is aborted. The logfile reads:

/var/log/syslog:Mar 28 21:32:23 valinor synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
/var/log/syslog:Mar 28 21:32:23 valinor pppd[8371]: pppd 2.4.4 started by root, uid 0
/var/log/syslog:Mar 28 21:32:23 valinor pppd[8371]: Serial connection established.
/var/log/syslog:Mar 28 21:32:23 valinor pppd[8371]: Using interface ppp0
/var/log/syslog:Mar 28 21:32:23 valinor pppd[8371]: Connect: ppp0 <--> /dev/ttyUSB0
/var/log/syslog:Mar 28 21:32:30 valinor pppd[8371]: Hangup (SIGHUP)
/var/log/syslog:Mar 28 21:32:30 valinor pppd[8371]: Modem hangup
/var/log/syslog:Mar 28 21:32:30 valinor pppd[8371]: Connection terminated.
/var/log/syslog:Mar 28 21:32:30 valinor pppd[8371]: Exit.

Or:

/var/log/syslog:Mar 28 22:21:48 valinor synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
/var/log/syslog:Mar 28 22:21:48 valinor pppd[19733]: pppd 2.4.4 started by root, uid 0
/var/log/syslog:Mar 28 22:21:48 valinor pppd[19733]: Device ttyUSB0 is locked by pid 19670
/var/log/syslog:Mar 28 22:21:48 valinor pppd[19733]: Exit.
/var/log/syslog:Mar 28 22:21:49 valinor pppd[19670]: Connect script failed
/var/log/syslog:Mar 28 22:21:49 valinor pppd[19670]: Exit.

If someone could please tell me what is wrong.

---

### Post by Tristan Schmelcher on 2007-11-03
I have a similar problem with my HTC TyTN II (Windows Mobile 6). The device shows that it is connecting and says "user authenticated". It then briefly switches to "connected" status (changing the "cancel" button to a "disconnect" button) but then the notice disappears. The errors I get in the log are:

Nov  3 16:52:28 tinygod3 synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Nov  3 16:52:28 tinygod3 pppd[3311]: pppd 2.4.4 started by root, uid 0
Nov  3 16:52:29 tinygod3 pppd[3311]: Serial connection established.
Nov  3 16:52:29 tinygod3 pppd[3311]: Using interface ppp0
Nov  3 16:52:29 tinygod3 pppd[3311]: Connect: ppp0 <--> /dev/ttyUSB0
Nov  3 16:52:29 tinygod3 pppd[3311]: Cannot determine ethernet address for proxy ARP
Nov  3 16:52:29 tinygod3 pppd[3311]: local  IP address 192.168.131.102
Nov  3 16:52:29 tinygod3 pppd[3311]: remote IP address 192.168.131.201
Nov  3 16:52:35 tinygod3 pppd[3311]: LCP terminated by peer
Nov  3 16:52:35 tinygod3 pppd[3311]: Connect time 0.1 minutes.
Nov  3 16:52:35 tinygod3 pppd[3311]: Sent 368 bytes, received 1018 bytes.
Nov  3 16:52:38 tinygod3 pppd[3311]: Connection terminated.
Nov  3 16:52:38 tinygod3 pppd[3311]: Modem hangup
Nov  3 16:52:38 tinygod3 pppd[3311]: Exit.

If I try to run any of the command-line tools (e.g., synce-pls), I get "Could not find configuration at path '(Default)'"

It's a shame, but I think that SynCE isn't really being maintained anymore, so it might simply be incompatible with our newer devices. :(

---

