---
title: "x11vnc server error end of stream"
date: 2008-07-25
forum: General Help
---

### Post by steve_d on 2008-07-25
I have 2 desktop installations of ubuntu 8.04 one acting as a server (fileshare, internet sharing, ftp ect) and the other acting as a workstation. 

I had x11vnc server setup and working perfectly on display 0 (although slow interface) and working for several days. I'm pretty sure I didn't modify anything that relates to it since then. Now when i try to connect with my vncviewer i get an error "End of stream". 

As of today when my server restarts i can't connect through vncviewer server:0 instead i have to ssh to the server, restart the xinetd service and then i can access the server via vncviewer.

I've tried adding a sleep 10/15/20 option to the xinetd.d script but that didn't do anything. Then i wrote a simple script to sleep for 10 then restart x11vnc and added it to the service boot sequence at 99. That hasen't proved useful either. I checked the logs under /var/logs/daemons.0 and it shows that my script worked by shutting down the service and restarting it, but to no avail.

Anyone have any ideas?

-Steve

Heres my log file, the time stamp is offset, so its definitely 'sleeping' or at least loading my script last. The last entry is me manually restarting it again, and my client can then connect:
```

Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jul 25 21:45:22 server xinetd[5349]: Reading included configuration file: /etc/xinetd.d/x11vnc [file=/etc/xinetd.d/x11vnc] [line=28]
Jul 25 21:45:22 server xinetd[5349]: removing chargen
Jul 25 21:45:22 server xinetd[5349]: removing chargen
Jul 25 21:45:22 server xinetd[5349]: removing daytime
Jul 25 21:45:22 server xinetd[5349]: removing daytime
Jul 25 21:45:22 server xinetd[5349]: removing discard
Jul 25 21:45:22 server xinetd[5349]: removing discard
Jul 25 21:45:22 server xinetd[5349]: removing echo
Jul 25 21:45:22 server xinetd[5349]: removing echo
Jul 25 21:45:22 server xinetd[5349]: removing time
Jul 25 21:45:22 server xinetd[5349]: removing time
Jul 25 21:45:22 server xinetd[5349]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Jul 25 21:45:22 server xinetd[5349]: Started working: 1 available service
Jul 25 21:45:24 server NetworkManager: <debug> [1217036724.373515] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_R___PX_W4824A'). 
Jul 25 21:45:24 server hcid[5481]: Bluetooth HCI daemon
Jul 25 21:45:24 server hcid[5481]: Starting SDP server
Jul 25 21:45:24 server hcid[5481]: Created local server at unix:abstract=/var/run/dbus-csdwlGrzWI,guid=123b0c0a08ca870bff2f017b488a81b4
Jul 25 21:45:24 server input[5497]: Bluetooth Input daemon
Jul 25 21:45:24 server input[5497]: Registered input manager path:/org/bluez/input
Jul 25 21:45:24 server audio[5498]: Bluetooth Audio daemon
Jul 25 21:45:24 server audio[5498]: Unix socket created: 5
Jul 25 21:45:24 server audio[5498]: audio.conf: Key file does not have key 'Enable'
Jul 25 21:45:24 server audio[5498]: audio.conf: Key file does not have key 'Disable'
Jul 25 21:45:24 server audio[5498]: add_service_record: got record id 0x10000
Jul 25 21:45:24 server audio[5498]: audio.conf: Key file does not have key 'Disable'
Jul 25 21:45:24 server audio[5498]: audio.conf: Key file does not have group 'A2DP'
Jul 25 21:45:24 server last message repeated 3 times
Jul 25 21:45:24 server audio[5498]: SEP 0x806d738 registered: type:0 codec:0 seid:1
Jul 25 21:45:24 server audio[5498]: add_service_record: got record id 0x10001
Jul 25 21:45:24 server audio[5498]: add_service_record: got record id 0x10002
Jul 25 21:45:24 server audio[5498]: add_service_record: got record id 0x10003
Jul 25 21:45:24 server audio[5498]: Registered manager path:/org/bluez/audio
Jul 25 21:45:24 server NetworkManager: <debug> [1217036724.684999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul 25 21:45:37 server xinetd[5349]: Exiting...
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jul 25 21:45:37 server xinetd[5732]: Reading included configuration file: /etc/xinetd.d/x11vnc [file=/etc/xinetd.d/x11vnc] [line=28]
Jul 25 21:45:37 server xinetd[5732]: removing chargen
Jul 25 21:45:37 server xinetd[5732]: removing chargen
Jul 25 21:45:37 server xinetd[5732]: removing daytime
Jul 25 21:45:37 server xinetd[5732]: removing daytime
Jul 25 21:45:37 server xinetd[5732]: removing discard
Jul 25 21:45:37 server xinetd[5732]: removing discard
Jul 25 21:45:37 server xinetd[5732]: removing echo
Jul 25 21:45:37 server xinetd[5732]: removing echo
Jul 25 21:45:37 server xinetd[5732]: removing time
Jul 25 21:45:37 server xinetd[5732]: removing time
Jul 25 21:45:37 server xinetd[5732]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Jul 25 21:45:37 server xinetd[5732]: Started working: 1 available service
Jul 25 21:57:25 server xinetd[5732]: Exiting...
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jul 25 21:57:25 server xinetd[5816]: Reading included configuration file: /etc/xinetd.d/x11vnc [file=/etc/xinetd.d/x11vnc] [line=28]
Jul 25 21:57:25 server xinetd[5816]: removing chargen
Jul 25 21:57:25 server xinetd[5816]: removing chargen
Jul 25 21:57:25 server xinetd[5816]: removing daytime
Jul 25 21:57:25 server xinetd[5816]: removing daytime
Jul 25 21:57:25 server xinetd[5816]: removing discard
Jul 25 21:57:25 server xinetd[5816]: removing discard
Jul 25 21:57:25 server xinetd[5816]: removing echo
Jul 25 21:57:25 server xinetd[5816]: removing echo
Jul 25 21:57:25 server xinetd[5816]: removing time
Jul 25 21:57:25 server xinetd[5816]: removing time
Jul 25 21:57:25 server xinetd[5816]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Jul 25 21:57:25 server xinetd[5816]: Started working: 1 available service
steve@server:/var/log$ 

```

---

### Post by krunge on 2008-07-26
What does the x11vnc log file say?  Including when you try to connect.

E.g. to get its output: x11vnc -o /tmp/x11vnc.log ...

---

### Post by steve_d on 2008-07-30
/var/log/x11vnc.log
```

29/07/2008 23:18:40 ***************************************
29/07/2008 23:18:40 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

```

I just tried adding the -create argument to the server args but same result returned:
```

steve@workstation:~$ vncviewer server:0

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Jul 30 13:20:37 2008
 CConn:       connected to host server port 5900
 main:        End of stream
steve@workstation:~$ 

```

EDIT:
This is what it says after I try to connect, and it fails
```

0/07/2008 13:21:03 HOME unset in -usepw mode.

```

---

### Post by krunge on 2008-07-30
I think you are trying too many things at once, trying to force it to work.

Is there even an X server running?  Is there one running when the system boots up?

---

### Post by steve_d on 2008-08-11
I'm pretty sure there was an X server running, meaning the GUI was loaded and sitting at the login screen.

I actually got tired of the random issues with vnc, and the really slow performance so I just shutdown gdm and run my server in CLI instead, and ssh into it whenever i need to do something.

At least its forcing me to learn :)

---

