---
title: "boot/reboot suspend problem"
date: 2018-09-06
forum: Hardware
---

### Post by robert129 on 2018-09-06
The system boots to (asus A0), when it is operating correctly.

It appears to be booting but blank screen (asus BIOS A0) sometimes. 

Sometimes it does not get past get past (asus BIOS d2 and 92) blank screen.

Changed HDMI leads, flashed BIOS changed CMOS battery with no effect on the problems.

Installed xUbuntu, Bionic 18.04 Ubuntu.

Have a Quadro 4000 card in a intel i7 -2600K 3.4Ghz machine

Boots and runs fine .... sometimes. When the system is properly up it does not have issues in operation. Does not shut down does not over heat.

Tried the nouveau drivers and nvidea proprietory. Now running Nouveau.

Light DM settings - all at never status with Display off

log files are attached which seem to show that lightdm is not starting is this causing the problem? Any ideas welcome?

---

### Post by robert129 on 2018-09-07
This machine was  working fine under window 10. Now the graphics card is messing with boot HDMI feed for audio and video.
Where should I look to start to nail down this issue with 18.04

---

### Post by robert129 on 2018-09-07
Seems that there is a problem with light manager before the system hangs - How do I make it start?


This is an extract of the log file: 



```
Sep 07 08:57:20 mars systemd[1]: lightdm.service: Service hold-off time over, sc
Sep 07 08:57:20 mars systemd[1]: lightdm.service: Scheduled restart job, restart
Sep 07 08:57:20 mars systemd[1]: Stopped Light Display Manager.
Sep 07 08:57:20 mars systemd[1]: gpu-manager.service: Start request repeated too
Sep 07 08:57:20 mars systemd[1]: gpu-manager.service: Failed with result 'start-
Sep 07 08:57:20 mars systemd[1]: Failed to start Detect the available GPUs and d
Sep 07 08:57:20 mars systemd[1]: lightdm.service: Start request repeated too qui
Sep 07 08:57:20 mars systemd[1]: lightdm.service: Failed with result 'exit-code'
Sep 07 08:57:20 mars systemd[1]: Failed to start Light Display Manager.
Sep 07 08:57:20 mars nm-dispatcher[734]: req:3 'connectivity-change': start runn
Sep 07 08:57:22 mars avahi-daemon[620]: Joining mDNS multicast group on interfac
Sep 07 08:57:22 mars avahi-daemon[620]: New relevant interface eno1.IPv6 for mDN
Sep 07 08:57:22 mars avahi-daemon[620]: Registering new address record for fe80:
Sep 07 08:57:23 mars NetworkManager[638]: <info>  [1536307043.5638] manager: sta
Sep 07 08:57:23 mars systemd[1]: Started Network Manager Wait Online.
Sep 07 08:57:23 mars systemd[1]: Reached target Network is Online.
Sep 07 08:57:23 mars systemd[1]: Starting Tool to automatically collect and subm
Sep 07 08:57:23 mars systemd[1]: Starting LSB: disk temperature monitoring daemo
Sep 07 08:57:23 mars systemd[1]: Started crash report submission daemon.
Sep 07 08:57:23 mars systemd[1]: kerneloops.service: Found left-over process 918
Sep 07 08:57:23 mars systemd[1]: This usually indicates unclean termination of a
Sep 07 08:57:23 mars systemd[1]: Started Tool to automatically collect and submi
Sep 07 08:57:23 mars systemd[1]: Started LSB: disk temperature monitoring daemon
Sep 07 08:57:23 mars systemd[1]: Reached target Multi-User System.
Sep 07 08:57:23 mars systemd[1]: Reached target Graphical Interface.
Sep 07 08:57:23 mars systemd[1]: Started Stop ureadahead data collection 45s aft
Sep 07 08:57:23 mars systemd[1]: Starting Update UTMP about System Runlevel Chan
Sep 07 08:57:23 mars systemd[1]: Started Update UTMP about System Runlevel Chang
Sep 07 08:57:23 mars systemd[1]: Startup finished in 3.149s (kernel) + 22.248s (
Sep 07 08:57:23 mars whoopsie[915]: [08:57:23] Using lock path: /var/lock/whoops
Sep 07 08:57:23 mars whoopsie[915]: [08:57:23] The default IPv4 route is: /org/f
Sep 07 08:57:23 mars whoopsie[915]: [08:57:23] Not a paid data plan: /org/freede
Sep 07 08:57:23 mars whoopsie[915]: [08:57:23] Found usable connection: /org/fre
Sep 07 08:57:43 mars systemd-timesyncd[580]: Synchronized to time server 91.189.
Sep 07 08:58:02 mars systemd-logind[624]: Power key pressed.
Sep 07 08:58:02 mars systemd-logind[624]: Powering Off...
Sep 07 08:58:02 mars systemd-logind[624]: System is powering down.
```

---

### Post by robert129 on 2018-09-07
x-0.log file:

```
(II) Server terminated successfully (0). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 04:58:36 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
resize called 1920 1080
resize called 1920 1080
(II) Server terminated successfully (0). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:17 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:17 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:18 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:18 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:18 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:19 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:19 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:19 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:20 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 08:57:20 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.


X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
Current Operating System: Linux mars 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=d462859b-f10a-495f-9f26-04dfae2ecfae ro quiet splash vt.handoff=1
Build Date: 13 April 2018  08:07:36PM
xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.34.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  7 09:01:04 2018
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
```

---

### Post by robert129 on 2018-09-07
lightdm.log:

```
[+11610.10s] DEBUG: Got signal 15 from process 1
[+11610.10s] DEBUG: Caught Terminated signal, shutting down
[+11610.10s] DEBUG: Stopping display manager
[+11610.10s] DEBUG: Seat seat0: Stopping
[+11610.10s] DEBUG: Seat seat0: Stopping display server
[+11610.10s] DEBUG: Sending signal 15 to process 840
[+11610.10s] DEBUG: Seat seat0: Stopping session
[+11610.10s] DEBUG: Terminating login1 session c1
[+11610.12s] DEBUG: Session pid=885: Sending SIGTERM
[+11610.12s] DEBUG: Session pid=885: Exited with return value 0
[+11610.12s] DEBUG: Seat seat0: Session stopped
[+11610.33s] DEBUG: Seat seat0 changes active session to 
[+11610.45s] DEBUG: Process 840 exited with return value 0
[+11610.45s] DEBUG: XServer 0: X server stopped
[+11610.45s] DEBUG: Releasing VT 7
[+11610.45s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+11610.45s] DEBUG: Seat seat0: Display server stopped
[+11610.45s] DEBUG: Seat seat0: Stopped
[+11610.45s] DEBUG: Display manager stopped
[+11610.45s] DEBUG: Stopping daemon
[+11610.45s] DEBUG: Exiting with return value 0
[+0.02s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=812
[+0.03s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.03s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.03s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.03s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.03s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.03s] DEBUG: Registered seat module local
[+0.03s] DEBUG: Registered seat module xremote
[+0.03s] DEBUG: Registered seat module unity
[+0.03s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.04s] DEBUG: Monitoring logind for seats
[+0.04s] DEBUG: New seat added from logind: seat0
[+0.04s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.04s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.04s] DEBUG: Seat seat0: Starting
[+0.04s] DEBUG: Seat seat0: Creating user session
[+0.04s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.04s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.06s] DEBUG: Seat seat0: Creating display server of type x
[+0.06s] DEBUG: Seat seat0: Plymouth is running on VT 1, but this is less than the configured minimum of 7 so not replacing it
[+0.06s] DEBUG: Quitting Plymouth
[+0.13s] DEBUG: Using VT 7
[+0.13s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.13s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.13s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.13s] DEBUG: XServer 0: Launching X Server
[+0.13s] DEBUG: Launching process 853: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.13s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.13s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.13s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.64s] DEBUG: Got signal 10 from process 853
[+2.64s] DEBUG: XServer 0: Got signal from X server :0
[+2.64s] DEBUG: XServer 0: Connecting to XServer :0
[+2.64s] DEBUG: Launching process 876: /sbin/prime-offload
[+2.67s] DEBUG: Process 876 exited with return value 0
[+2.67s] DEBUG: Seat seat0: Exit status of /sbin/prime-offload: 0
[+2.67s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+2.67s] DEBUG: Session pid=881: Started with service 'lightdm-autologin', username 'rob'
[+2.75s] DEBUG: Session pid=881: Authentication complete with return value 0: Success
[+2.75s] DEBUG: Seat seat0: Session authenticated, running command
[+2.75s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+2.75s] DEBUG: Session pid=881: Running command /usr/sbin/lightdm-session startxfce4
[+2.75s] DEBUG: Creating shared data directory /var/lib/lightdm-data/rob
[+2.75s] DEBUG: Session pid=881: Logging to .xsession-errors
[+3.31s] DEBUG: Activating VT 7
[+3.31s] DEBUG: Activating login1 session c1
[+3.31s] DEBUG: Seat seat0 changes active session to c1
[+3.31s] DEBUG: Session c1 is already active
[+14266.21s] DEBUG: Got signal 15 from process 1
[+14266.21s] DEBUG: Caught Terminated signal, shutting down
[+14266.21s] DEBUG: Stopping display manager
[+14266.21s] DEBUG: Seat seat0: Stopping
[+14266.21s] DEBUG: Seat seat0: Stopping display server
[+14266.21s] DEBUG: Sending signal 15 to process 853
[+14266.21s] DEBUG: Seat seat0: Stopping session
[+14266.21s] DEBUG: Terminating login1 session c1
[+14266.23s] DEBUG: Session pid=881: Sending SIGTERM
[+14266.26s] DEBUG: Session pid=881: Exited with return value 0
[+14266.26s] DEBUG: Seat seat0: Session stopped
[+14266.40s] DEBUG: Seat seat0 changes active session to 
[+14266.60s] DEBUG: Process 853 exited with return value 0
[+14266.60s] DEBUG: XServer 0: X server stopped
[+14266.60s] DEBUG: Releasing VT 7
[+14266.60s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+14266.60s] DEBUG: Seat seat0: Display server stopped
[+14266.60s] DEBUG: Seat seat0: Stopped
[+14266.60s] DEBUG: Display manager stopped
[+14266.60s] DEBUG: Stopping daemon
[+14266.60s] DEBUG: Exiting with return value 0
[+0.02s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.02s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=733
[+0.02s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.02s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.02s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.02s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.02s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.02s] DEBUG: Registered seat module local
[+0.02s] DEBUG: Registered seat module xremote
[+0.02s] DEBUG: Registered seat module unity
[+0.02s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Monitoring logind for seats
[+0.03s] DEBUG: New seat added from logind: seat0
[+0.03s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.03s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.03s] DEBUG: Seat seat0: Starting
[+0.03s] DEBUG: Seat seat0: Creating user session
[+0.03s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.03s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.05s] DEBUG: Seat seat0: Creating display server of type x
[+0.05s] DEBUG: Seat seat0: Plymouth is running on VT 1, but this is less than the configured minimum of 7 so not replacing it
[+0.05s] DEBUG: Quitting Plymouth
[+0.07s] DEBUG: Using VT 7
[+0.07s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.07s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.07s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.07s] DEBUG: XServer 0: Launching X Server
[+0.07s] DEBUG: Launching process 746: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.07s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.07s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.07s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.78s] DEBUG: Process 746 terminated with signal 6
[+0.78s] DEBUG: XServer 0: X server stopped
[+0.78s] DEBUG: Releasing VT 7
[+0.78s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.78s] DEBUG: Seat seat0: Display server stopped
[+0.78s] DEBUG: Seat seat0: Stopping session
[+0.78s] DEBUG: Seat seat0: Session stopped
[+0.78s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.78s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+0.78s] DEBUG: Seat seat0: Creating greeter session
[+0.79s] DEBUG: Seat seat0: Creating display server of type x
[+0.79s] DEBUG: Using VT 7
[+0.79s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.79s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.79s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.79s] DEBUG: XServer 0: Launching X Server
[+0.79s] DEBUG: Launching process 767: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.79s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.91s] DEBUG: Process 767 terminated with signal 6
[+0.91s] DEBUG: XServer 0: X server stopped
[+0.91s] DEBUG: Releasing VT 7
[+0.91s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.91s] DEBUG: Seat seat0: Display server stopped
[+0.91s] DEBUG: Seat seat0: Stopping session
[+0.91s] DEBUG: Seat seat0: Session stopped
[+0.91s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.91s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.91s] DEBUG: Seat seat0: Stopping
[+0.91s] DEBUG: Seat seat0: Stopped
[+0.91s] DEBUG: Required seat has stopped
[+0.91s] DEBUG: Stopping display manager
[+0.91s] DEBUG: Display manager stopped
[+0.91s] DEBUG: Stopping daemon
[+0.91s] DEBUG: Exiting with return value 1
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=782
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Monitoring logind for seats
[+0.01s] DEBUG: New seat added from logind: seat0
[+0.01s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.01s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.01s] DEBUG: Seat seat0: Starting
[+0.01s] DEBUG: Seat seat0: Creating user session
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.02s] DEBUG: Seat seat0: Creating display server of type x
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.02s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: XServer 0: Launching X Server
[+0.02s] DEBUG: Launching process 787: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.02s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.16s] DEBUG: Process 787 terminated with signal 6
[+0.16s] DEBUG: XServer 0: X server stopped
[+0.16s] DEBUG: Releasing VT 7
[+0.16s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.16s] DEBUG: Seat seat0: Display server stopped
[+0.16s] DEBUG: Seat seat0: Stopping session
[+0.16s] DEBUG: Seat seat0: Session stopped
[+0.16s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.16s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+0.16s] DEBUG: Seat seat0: Creating greeter session
[+0.16s] DEBUG: Seat seat0: Creating display server of type x
[+0.16s] DEBUG: Using VT 7
[+0.16s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.16s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.16s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.16s] DEBUG: XServer 0: Launching X Server
[+0.16s] DEBUG: Launching process 789: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.16s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.29s] DEBUG: Process 789 terminated with signal 6
[+0.29s] DEBUG: XServer 0: X server stopped
[+0.29s] DEBUG: Releasing VT 7
[+0.29s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.29s] DEBUG: Seat seat0: Display server stopped
[+0.29s] DEBUG: Seat seat0: Stopping session
[+0.29s] DEBUG: Seat seat0: Session stopped
[+0.29s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.29s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.29s] DEBUG: Seat seat0: Stopping
[+0.29s] DEBUG: Seat seat0: Stopped
[+0.29s] DEBUG: Required seat has stopped
[+0.29s] DEBUG: Stopping display manager
[+0.29s] DEBUG: Display manager stopped
[+0.29s] DEBUG: Stopping daemon
[+0.29s] DEBUG: Exiting with return value 1
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=803
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Monitoring logind for seats
[+0.01s] DEBUG: New seat added from logind: seat0
[+0.01s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.01s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.01s] DEBUG: Seat seat0: Starting
[+0.01s] DEBUG: Seat seat0: Creating user session
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.02s] DEBUG: Seat seat0: Creating display server of type x
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.02s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: XServer 0: Launching X Server
[+0.02s] DEBUG: Launching process 808: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.02s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.15s] DEBUG: Process 808 terminated with signal 6
[+0.15s] DEBUG: XServer 0: X server stopped
[+0.15s] DEBUG: Releasing VT 7
[+0.15s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.15s] DEBUG: Seat seat0: Display server stopped
[+0.15s] DEBUG: Seat seat0: Stopping session
[+0.15s] DEBUG: Seat seat0: Session stopped
[+0.15s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.15s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+0.15s] DEBUG: Seat seat0: Creating greeter session
[+0.15s] DEBUG: Seat seat0: Creating display server of type x
[+0.15s] DEBUG: Using VT 7
[+0.15s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.15s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.15s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.15s] DEBUG: XServer 0: Launching X Server
[+0.15s] DEBUG: Launching process 810: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.15s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.29s] DEBUG: Process 810 terminated with signal 6
[+0.29s] DEBUG: XServer 0: X server stopped
[+0.29s] DEBUG: Releasing VT 7
[+0.29s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.29s] DEBUG: Seat seat0: Display server stopped
[+0.29s] DEBUG: Seat seat0: Stopping session
[+0.29s] DEBUG: Seat seat0: Session stopped
[+0.29s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.29s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.29s] DEBUG: Seat seat0: Stopping
[+0.29s] DEBUG: Seat seat0: Stopped
[+0.29s] DEBUG: Required seat has stopped
[+0.29s] DEBUG: Stopping display manager
[+0.29s] DEBUG: Display manager stopped
[+0.29s] DEBUG: Stopping daemon
[+0.29s] DEBUG: Exiting with return value 1
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=824
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Monitoring logind for seats
[+0.01s] DEBUG: New seat added from logind: seat0
[+0.01s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.01s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.01s] DEBUG: Seat seat0: Starting
[+0.01s] DEBUG: Seat seat0: Creating user session
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.02s] DEBUG: Seat seat0: Creating display server of type x
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.02s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: XServer 0: Launching X Server
[+0.02s] DEBUG: Launching process 829: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.02s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.15s] DEBUG: Process 829 terminated with signal 6
[+0.15s] DEBUG: XServer 0: X server stopped
[+0.15s] DEBUG: Releasing VT 7
[+0.15s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.15s] DEBUG: Seat seat0: Display server stopped
[+0.15s] DEBUG: Seat seat0: Stopping session
[+0.15s] DEBUG: Seat seat0: Session stopped
[+0.15s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.15s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+0.15s] DEBUG: Seat seat0: Creating greeter session
[+0.15s] DEBUG: Seat seat0: Creating display server of type x
[+0.15s] DEBUG: Using VT 7
[+0.15s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.15s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.15s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.15s] DEBUG: XServer 0: Launching X Server
[+0.15s] DEBUG: Launching process 831: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.15s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.29s] DEBUG: Process 831 terminated with signal 6
[+0.29s] DEBUG: XServer 0: X server stopped
[+0.29s] DEBUG: Releasing VT 7
[+0.29s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.29s] DEBUG: Seat seat0: Display server stopped
[+0.29s] DEBUG: Seat seat0: Stopping session
[+0.29s] DEBUG: Seat seat0: Session stopped
[+0.29s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.29s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.29s] DEBUG: Seat seat0: Stopping
[+0.29s] DEBUG: Seat seat0: Stopped
[+0.29s] DEBUG: Required seat has stopped
[+0.29s] DEBUG: Stopping display manager
[+0.29s] DEBUG: Display manager stopped
[+0.29s] DEBUG: Stopping daemon
[+0.29s] DEBUG: Exiting with return value 1
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=845
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Registered seat module local
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Monitoring logind for seats
[+0.01s] DEBUG: New seat added from logind: seat0
[+0.01s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.01s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.01s] DEBUG: Seat seat0: Starting
[+0.01s] DEBUG: Seat seat0: Creating user session
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.01s] DEBUG: Seat seat0: Creating display server of type x
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.01s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: XServer 0: Launching X Server
[+0.01s] DEBUG: Launching process 850: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.15s] DEBUG: Process 850 terminated with signal 6
[+0.15s] DEBUG: XServer 0: X server stopped
[+0.15s] DEBUG: Releasing VT 7
[+0.15s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.15s] DEBUG: Seat seat0: Display server stopped
[+0.15s] DEBUG: Seat seat0: Stopping session
[+0.15s] DEBUG: Seat seat0: Session stopped
[+0.15s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.15s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+0.15s] DEBUG: Seat seat0: Creating greeter session
[+0.15s] DEBUG: Seat seat0: Creating display server of type x
[+0.15s] DEBUG: Using VT 7
[+0.15s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.15s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.15s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.15s] DEBUG: XServer 0: Launching X Server
[+0.15s] DEBUG: Launching process 852: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.15s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.29s] DEBUG: Process 852 terminated with signal 6
[+0.29s] DEBUG: XServer 0: X server stopped
[+0.29s] DEBUG: Releasing VT 7
[+0.29s] DEBUG: XServer 0: Removing X server authority /var/run/lightdm/root/:0
[+0.29s] DEBUG: Seat seat0: Display server stopped
[+0.29s] DEBUG: Seat seat0: Stopping session
[+0.29s] DEBUG: Seat seat0: Session stopped
[+0.29s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+0.29s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
[+0.29s] DEBUG: Seat seat0: Stopping
[+0.29s] DEBUG: Seat seat0: Stopped
[+0.29s] DEBUG: Required seat has stopped
[+0.29s] DEBUG: Stopping display manager
[+0.29s] DEBUG: Display manager stopped
[+0.29s] DEBUG: Stopping daemon
[+0.29s] DEBUG: Exiting with return value 1
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.09s] DEBUG: Starting Light Display Manager 1.26.0, UID=0 PID=794
[+0.09s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.09s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration
[+0.09s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.09s] DEBUG: Registered seat module local
[+0.09s] DEBUG: Registered seat module xremote
[+0.09s] DEBUG: Registered seat module unity
[+0.09s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.09s] DEBUG: Monitoring logind for seats
[+0.09s] DEBUG: New seat added from logind: seat0
[+0.09s] WARNING: Seat type 'xlocal' is deprecated, use 'type=local' instead
[+0.09s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.09s] DEBUG: Seat seat0: Starting
[+0.09s] DEBUG: Seat seat0: Creating user session
[+0.09s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.09s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.11s] DEBUG: Seat seat0: Creating display server of type x
[+0.11s] DEBUG: Seat seat0: Plymouth is running on VT 1, but this is less than the configured minimum of 7 so not replacing it
[+0.11s] DEBUG: Quitting Plymouth
[+0.14s] DEBUG: Using VT 7
[+0.14s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.14s] DEBUG: XServer 0: Logging to /var/log/lightdm/x-0.log
[+0.14s] DEBUG: XServer 0: Writing X server authority to /var/run/lightdm/root/:0
[+0.14s] DEBUG: XServer 0: Launching X Server
[+0.14s] DEBUG: Launching process 813: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.14s] DEBUG: XServer 0: Waiting for ready signal from X server :0
[+0.14s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.14s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.36s] DEBUG: Got signal 10 from process 813
[+2.36s] DEBUG: XServer 0: Got signal from X server :0
[+2.36s] DEBUG: XServer 0: Connecting to XServer :0
[+2.37s] DEBUG: Launching process 832: /sbin/prime-offload
[+2.41s] DEBUG: Process 832 exited with return value 0
[+2.41s] DEBUG: Seat seat0: Exit status of /sbin/prime-offload: 0
[+2.41s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+2.41s] DEBUG: Session pid=837: Started with service 'lightdm-autologin', username 'rob'
[+2.50s] DEBUG: Session pid=837: Authentication complete with return value 0: Success
[+2.50s] DEBUG: Seat seat0: Session authenticated, running command
[+2.50s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+2.50s] DEBUG: Session pid=837: Running command /usr/sbin/lightdm-session startxfce4
[+2.50s] DEBUG: Creating shared data directory /var/lib/lightdm-data/rob
[+2.50s] DEBUG: Session pid=837: Logging to .xsession-errors
[+3.03s] DEBUG: Activating VT 7
[+3.03s] DEBUG: Activating login1 session c1
[+3.03s] DEBUG: Seat seat0 changes active session to c1
[+3.03s] DEBUG: Session c1 is already active
```

---

### Post by robert129 on 2018-09-08
Bump

---

### Post by QIII on 2018-09-08
Please enclose all commands and their results in code tags.  That will preserve formatting and make your post easier to read.

---

### Post by robert129 on 2018-09-09
moved the graphics card to slot 3 of 4 .... hunky dory ... go figure ... the only slot that it boots in persistently without issue!

---

