---
title: "vnc4 and xinetd"
date: 2005-11-16
forum: General Help
---

### Post by pjstadig on 2005-11-16
I have followed the instructions in [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638) and xinetd will not start vnc4server. When I do an nmap port scan I get nothing:

```
$ nmap localhost

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-11-16 14:27 EST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
631/tcp   open  ipp
32770/tcp open  sometimes-rpc3

Nmap finished: 1 IP address (1 host up) scanned in 0.139 seconds

```

When I try to connect with xvnc4viewer I get nothing:

```
$ xvnc4viewer localhost:1

VNC viewer for X version 4.0 - built Apr 19 2005 04:20:29
Copyright (C) 2002-2004 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Nov 16 14:30:42 2005
 main:        unable to connect to host: Connection refused (111)

```

If I start the vnc server at the command line it starts with no problem:

```
$ vnc4server

New 'stadig:1 (pstadig)' desktop is stadig:1

Starting applications specified in /home/pstadig/.vnc/xstartup
Log file is /home/pstadig/.vnc/stadig:1.log

```

Then if I do ```
xvnc4viewer localhost:1
``` I get connected.  What's the deal? Why won't xinetd start my vnc server?

/etc/services
```
...snip...
# Local services
vnc1024		5901/tcp			# VNC

```

/etc/xinetd.conf
```
..snip..
service vnc1024 {
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}
..snip..
```

---

### Post by vedder on 2005-12-12
i have the same problem.... any answers? :confused: :rolleyes:

---

### Post by pjstadig on 2005-12-13
Lesson: check logs

I figured it out. I was getting the following error from xinetd in my /var/log/syslog

> Dec 13 19:13:56 localhost xinetd[9234]: Service vnc1024: missing '{' [file=/etc/xinetd.conf] [line=10]


I needed to change
> service vnc1024 {
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}

to 

> service vnc1024
{
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}

because the opening brace must not be on the same line as the service name. It should be on a separate line.

Paul

---

