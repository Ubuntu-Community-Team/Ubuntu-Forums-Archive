---
title: "ntpd synchronization problem"
date: 2008-07-28
forum: General Help
---

### Post by VictorR on 2008-07-28
There was always the problem of time synchronization on my computer, which I can't resolve yet. In short words the problem is that ntpd starts earlier and gives up well before USB ADSL modem can connect to the Internet.
Details: OS Ubuntu 8.04, USB ADSL modem SpeedTouch 330. Below is the extracts from system log:
```

Jul 29 10:47:35 ubuntu-desktop kernel: [   55.122418] ATM dev 0: ADSL line is synchronising
Jul 29 10:47:35 ubuntu-desktop nss_wins[3491]: can't find host nz.pool.ntp.org 
Jul 29 10:47:36 ubuntu-desktop nss_wins[3491]: no servers can be used, exiting
Jul 29 10:47:36 ubuntu-desktop NetworkManager: <info>  starting... 
Jul 29 10:47:36 ubuntu-desktop ntpd[5314]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: precision = 1.000 usec
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #1 wildcard, ::#123 Disabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #2 lo, ::1#123 Enabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #3 eth0, fe80::20c:76ff:fece:eeb5#123 Enabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: Listening on interface #5 eth0, 192.168.0.1#123 Enabled
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: kernel time sync status 0040
Jul 29 10:47:36 ubuntu-desktop ntpd[5325]: frequency initialized -25.917 PPM from /var/lib/ntp/ntp.drift
...
...
Jul 29 10:47:41 ubuntu-desktop ntpd_initres[5727]: host name not found: nz.pool.ntp.org
Jul 29 10:47:41 ubuntu-desktop ntpd_initres[5727]: couldn't resolve `nz.pool.ntp.org', giving up on it
...
...
Jul 29 10:47:53 ubuntu-desktop kernel: [   73.146685] PPP generic driver version 2.4.2
Jul 29 10:48:00 ubuntu-desktop kernel: [   80.107190] ATM dev 0: ADSL line is up (7232 kb/s down | 160 kb/s up)
Jul 29 10:48:01 ubuntu-desktop pppd[6714]: Plugin pppoatm.so loaded.
Jul 29 10:48:01 ubuntu-desktop pppd[6714]: pppd 2.4.4 started by root, uid 0
Jul 29 10:48:01 ubuntu-desktop pppd[6714]: using channel 1
Jul 29 10:48:01 ubuntu-desktop pppd[6714]: Using interface ppp0
Jul 29 10:48:01 ubuntu-desktop pppd[6714]: Connect: ppp0 <--> 0.100
...
Jul 29 10:48:05 ubuntu-desktop pppd[6764]: Plugin pppoatm.so loaded.
Jul 29 10:48:05 ubuntu-desktop pppd[6764]: pppd 2.4.4 started by root, uid 0
Jul 29 10:48:05 ubuntu-desktop pppd[6764]: connect(0.100): Address already in use
Jul 29 10:48:05 ubuntu-desktop pppd[6764]: Exit.

```
As it can be seen from the above the modem started working at about 10:47:35, but finally established the connection by 10:48:05 only, while ntpd gave up at 10:47:41. After this the ntp daemon does not make any attempts to synchronize time. To bring back to life ntpd I have to go to Time Synchronization menu, set Manual mode (this assumably terminates the daemon), then switch back to "Synchronize with Time Servers" to restart it.

Does anybody know the better way to deal with this? I mean to change the order which daemons start in or somehow to force ntpd to synchronize, say, 1 minute after the system fully loaded?

Thanks in advance.

---

### Post by RealPSL on 2008-07-28
What is giving up on the startup is the initial ntpdate that fixes large time gaps. However the ntpd daemon when running will continue to make little adjustments to your time to match that of your ntp servers as the time passes. Point is unless your time is off by a significantly large amount that initial failure is not a concern.

---

### Post by VictorR on 2008-07-29
Unfortunately it does not look like this. The problem is that ntpd never tries to connect to time servers, if it failed at startup. I see it from the daemon.log (actually don't see, unless I re-started the daemon, as I described in my inintal post).

---

### Post by Mister.Vash on 2008-07-29
The easiest way might be to setup a script that start it if it isn't running

[https://help.ubuntu.com/community/UbuntuTime?highlight=(ntpd)#Is%20NTP%20running?](https://help.ubuntu.com/community/UbuntuTime?highlight=(ntpd)#Is%20NTP%20running?)

If that doesn't do it, post again as there are plenty of different ways to do it

---

### Post by VictorR on 2008-07-29
Thanks, this seems to be exactly what I was looking for.

---

