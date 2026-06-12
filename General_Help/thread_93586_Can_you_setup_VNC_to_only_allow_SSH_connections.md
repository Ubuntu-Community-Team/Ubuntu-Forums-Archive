---
title: "Can you setup VNC to only allow SSH connections?"
date: 2005-11-22
forum: General Help
---

### Post by ringding on 2005-11-22
I can setup VNC to tunnel SSH sessions but I can still connect without SSH.

I was wondering if anyone has had experience setting up VNC to only allow SSH connections? If so, how did you do it?

Thanks!!

---

### Post by ringding on 2005-11-23
Anyone?

---

### Post by soulestream on 2005-11-23
memory serves me, you setup VNC to only accept local connections

that way any connection from remote are declined, ssh is viewed as a local connection, so it is accepted.


hope that helps

soule

---

### Post by ringding on 2005-11-23
I will definitly give that a shot.........sounds fairly easy........

THANKS MUCH!!

---

### Post by redchair on 2008-04-08
This was a useful thread: but another question. I am running tightvncserver with the vncserver command (which is eventualy linked to the tightvncserver command). However in either case there is a second port on LISTEN status  (TCP *:x11-1 which is equivalent to TCP *:6001). Is there any way to allow listening only on localhost on the 6001 port?

I am able to use the commands

$  vncserver :1 -localhost
$ lsof -i
output is
Xtightvnc 5323    user    0u  IPv4  16167       TCP *:x11-1 (LISTEN)
Xtightvnc 5323    user   3u  IPv4  16170       TCP localhost:5901 (LISTEN)

$  vncserver :1
$ lsof -i
Xtightvnc 5415    user    0u  IPv4  16864       TCP *:x11-1 (LISTEN)
Xtightvnc 5415    user   3u  IPv4  16867       TCP *:5901 (LISTEN)

Killing the Xtightvnc process kills all listening on both ports.
======April 14, 2008=========
Thanks for the replies below. There is an undocumented option on vncserver (at least not included in my man page) -nolisten tcp. The full command that will allow connections from localhost only without the extra "x11-1" port listening is:
$  vncserver :1 -localhost -nolisten tcp

---

### Post by bodhi.zazen on 2008-04-08
I am not sure about vnc , have you considered using a firewall ? iptables (configured with firestarter) would take care of this for you.

---

### Post by HermanAB on 2008-04-08
You can drop the VNC ports with IPtables.

However, consider this:
Since you now have SSH running, why do you still bother with VNC?

VNC and SSH do the same things, with the big difference that SSH is secure.  Tunneling VNC over SSH is redundant and slow.  Just use SSH:
$ ssh user@server "gedit filename"

If you are so inclined then you could even run the toolbar and then just point and click:
$ ssh user@server "gnome-panel"
$ ssh user@server "kicker"

Cheers,

Herman

---

### Post by redchair on 2008-04-14
HermanAB,

That sounds like a streamlined and efficient solution to just use SSH. However I am not experienced in getting SSH to do display tasks.

With VNC over SSH I am sure of what it does: it produces a service that listens on one port (on localhost[server] only), provides password protection to that port to prevent snooping by (non admin) users on the server, and transmits a compressed video stream over a SSH connection to a window in my remote linux window manager (fluxbox) . [Mouse clicks are also received over the same connection.]

It sounds like an interesting solution though, if I can launch any remote x application locally. Is this "x forwarding"?  However I think another advantage may be that I can VNC over SSH from a Windows or Mac computer not running an x-server, and not require the x11 environment, gnome, or kde to be installed.

SSH alone might provide equivalent services and better performance, however I just haven't gotten around to trying it yet. I will try it when I have more time. Probably I will have start at this guide:
[http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html#s5.4](http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html#s5.4)
---------------------
 5.3 Securing access to the X Window System

Today, X terminals are used by more and more companies where one server is needed for a lot of workstations. This can be dangerous, because you need to allow the file server to connect to the the clients (X server from the X point of view. X switches the definition of client and server). If you follow the (very bad) suggestion of many docs, you type xhost + on your machine. This allows any X client to connect to your system. For slightly better security, you can use the command xhost +hostname instead to only allow access from specific hosts.

A much more secure solution, though, is to use ssh to tunnel X and encrypt the whole session. This is done automatically when you ssh to another machine. This has to be enabled in /etc/ssh/ssh_config by setting X11Forwarding to yes. In times of SSH, you should drop the xhost based access control completely.

For best security, if you do not need X access from other machines, is to switch off the binding on tcp port 6000 simply by typing: startx -- -nolisten tcp
----------------------------------------------

---

