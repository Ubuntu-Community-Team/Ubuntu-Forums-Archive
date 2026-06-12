---
title: "startx problem"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by jose3 on 2006-07-08
Hi guys I cannot startx here is my log.

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux PERON 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 13:41:15 2006
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
        Undefined InputDevice "Configured Mouse" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

```

I believe this is the problem, the mouse. 
```

Undefined InputDevice "Configured Mouse" referenced by ServerLayout "Default Layout".

```

I am trying to use a serial mouse. This is what I have in /etc/X11/xorg.conf.
```

Section "InputDevice"
        Identifier "Serial Mouse"
        Driver "mouse"
        Option "Protocol" "Microsoft"
        Option "Device" "/dev/ttyS1"
        Option "SendCoreEvents" "true"
        Option "Emulate3Buttons" "true"
        Option "Emulate3Timeout" "70"
EndSection

```

I am diagnosing right this problem?. I am using the correct InputDevice I belive.
Thanks very much in advance guys.

---

