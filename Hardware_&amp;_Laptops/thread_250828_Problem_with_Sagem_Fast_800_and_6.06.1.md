---
title: "Problem with Sagem Fast 800 and 6.06.1"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by pstratos on 2006-09-04
Hello All

This is my first post...

I am trying to switch to Ubuntu from Windows. 

It is a whole month (during which I have read countless forums and howtos), that I am trying to install correctly the Sagem modem. Under Windows the modem is operating with no problems at all.

My details are:
Ubuntu 6.06.1 with Kernel: 2.6.15-26-686
Modem: Sagem Fast 800 (Line: POTS)
ISP: otenet (Greece) with connection: 384/128kbps (OnDSL Kit)

I have installed both file: [COLOR="Red"]ueagle-atm-1.3.tar.gz[/COLOR] and [COLOR="Red"]ueagle-data-1.1.tar.gz[/COLOR], with no problems displayed in the console (following the installation procedure indicated by aces21 in [http://ubuntuforums.org/showthread.php?t=201127)](http://ubuntuforums.org/showthread.php?t=201127)). 
(the only thing that is clear from the forums is that I should not install [COLOR="Red"]eagle-usb-2.3.2.tar.bz2[/COLOR]).

(I have repeated the installation procedure more than 20 times, with always the same results)

The single-line contents of both my pap-secrets and chap-secrets files, which are identical are:

```
"xxxxx@otenet.gr" "*" "xxxxxx" "*"

```

( I have deleted - as a thread suggested - the initial contents of the pap-secrets file!!!)

BTW what are the correct permissions of both these files: 600 or 740? There is divergence among different forums and how-tos.

The contents of my [COLOR="Red"]ueagle-atm[/COLOR] file are:

```
user "xxxxx@otenet.gr"
plugin pppoatm.so 8.35
noipdefault
usepeerdns
defaultroute
persist
noauth

```

I am getting the following console output:

```
stratos@stratos:~$  dmesg|grep ueagle
[17179592.576000] [ueagle-atm] driver ueagle-gna 1.3 loaded
[17179592.576000] usb 1-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9031) : Eagle III
[17179592.892000] usb 1-2: [ueagle-atm] using iso mode
[17179592.892000] usb 1-2: [ueagle-atm] (re)booting started
[17179592.892000] usb 1-2: [ueagle-atm] created proc entry at: /proc/driver/ueagle-atm/001-003
[17179592.892000] usbcore: registered new driver ueagle-atm
[17179605.896000] usb 1-2: [ueagle-atm] modem operational
[17179605.904000] usb 1-2: [ueagle-atm] ATU-R firmware version : 44e2ea17

```

```
stratos@stratos:~$ sudo modprobe pppoatm
stratos@stratos:~$ pon ueagle-atm
Plugin pppoatm.so loaded.

```

```
stratos@stratos:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4068 (3.9 KiB)  TX bytes:4068 (3.9 KiB)

```

```
stratos@stratos:~$ plog
Sep  4 22:12:40 stratos pppd[5460]: Plugin pppoatm.so loaded.
Sep  4 22:12:40 stratos pppd[5462]: pppd 2.4.4b1 started by stratos, uid 1000
Sep  4 22:12:40 stratos pppd[5462]: Using interface ppp0
Sep  4 22:12:40 stratos pppd[5462]: Connect: ppp0 <--> 8.35

```

```
stratos@stratos:~$ sudo poff ueagle-atm
stratos@stratos:~$ plog
Sep  4 22:12:40 stratos pppd[5460]: Plugin pppoatm.so loaded.
Sep  4 22:12:40 stratos pppd[5462]: pppd 2.4.4b1 started by stratos, uid 1000
Sep  4 22:12:40 stratos pppd[5462]: Using interface ppp0
Sep  4 22:12:40 stratos pppd[5462]: Connect: ppp0 <--> 8.35
Sep  4 22:15:41 stratos pppd[5462]: Terminating on signal 15
Sep  4 22:15:41 stratos pppd[5462]: Connection terminated.
Sep  4 22:15:41 stratos pppd[5462]: Exit.

```

```
stratos@stratos:~$ tail /var/log/syslog
Sep  4 22:12:15 stratos kernel: [17180790.204000] CSLIP: code copyright 1989 Regents of the University of California
Sep  4 22:12:15 stratos kernel: [17180790.220000] PPP generic driver version 2.4.2
Sep  4 22:12:40 stratos pppd[5460]: Plugin pppoatm.so loaded.
Sep  4 22:12:40 stratos pppd[5462]: pppd 2.4.4b1 started by stratos, uid 1000
Sep  4 22:12:40 stratos pppd[5462]: Using interface ppp0
Sep  4 22:12:40 stratos pppd[5462]: Connect: ppp0 <--> 8.35
Sep  4 22:15:41 stratos pppd[5462]: Terminating on signal 15
Sep  4 22:15:41 stratos pppd[5462]: Connection terminated.
Sep  4 22:15:41 stratos pppd[5462]: Exit.

```

I have no indication on what I should do next, in order to connect. I hope that it is a configuration issue...

Shall I have to install PPPoE?

Shall I have to install the CMV files manually or extract them from the windows installation?

Shall I try the new version of  [COLOR="Red"]eagle-usb-2.3.3.tar.bz2[/COLOR]?

Any help will be greatly appreciated...(I apologize for the long console output).

Thanks in advance.

email: ep112358_at_gmail.com

---

