---
title: "xdmcp won't let me log in."
date: 2005-11-12
forum: General Help
---

### Post by Rizado on 2005-11-12
I've been trying to log in to my ubuntucomp from windows through cygwin. I enabled xdmcp in my gdm.conf and gdm is showing but when i try to log in gnome won't start. If I choose failsafe I get a xterm and from that I can start apps but whenever I choose gnome I just get a brown screen :confused:

---

### Post by wujek on 2005-11-12
ubuntucomp:
    netstat -ant
check, if exist lines with 6000, 7100 (7300)
if not > check gdm.conf and fs.conf
next
    netstat -anu
check, if exist line with 177
And check, if ports 6000, 7100 (TCP) and port 177 (UDP) are opened by windows firewall.

---

### Post by Rizado on 2005-11-13
6000 is there, 177 too but not 7000 or 7300.
Where is fs.conf and what is it?

---

### Post by wujek on 2005-11-13
fs.conf - Fonts Server (xfs) config file 
check, if exists
     /etc/init.d/xfs
if not > install xfs
     apt-get install xfs
Fonts Server - needed for XDMCP session.

---

### Post by jesterfred on 2005-11-18
[QUOTE=Rizado]I've been trying to log in to my ubuntucomp from windows through cygwin. I enabled xdmcp in my gdm.conf and gdm is showing but when i try to log in gnome won't start. If I choose failsafe I get a xterm and from that I can start apps but whenever I choose gnome I just get a brown screen :confused:[/QUOTE]

If you wait for 5 minutes, does the login complete?  I am able to use Xnest from Ubuntu to login to an Unbutu via XDMCP - but the login takes an extremely long time.  The behavior I see is:  The login screen shows up quickly.  After I type in a username and password, there is a long pause - minutes - before the desktop shows.

Perhaps this is a sound device ownership problem?  Login is trying to play the log in sound?

---

### Post by f3rrix on 2006-06-23
For those who are experiencing this "slowness after login" thing with xdmcp and gdm/gnome, this is what's going on:

The sound driver (ESD) is trying to connect to your desktop over TCP/16001, and getting no reply.  If it was simply a closed port it would fail right away and maybe work then, but when it gets no reply it sits there waiting for a long time, and then it retries, and retries... for EVERY SOUND it wants to play.

The quick and dirty solution is to log in to the console and disable ESD (via your preferences, sound control panel).

Then your remote sessions will work great.

I hear there's a cygwin port of ESD, so it might be possible to actually RUN the sound daemon, and get remote sounds (c00l).

It is possible that if you open inbound 16001/tcp on your desktop firewall it *could* start going fast.  But on my windows XP service-pack-2, it just does the "no response" behavior I mentioned above.

I have spent all night trying to figure this out, so I hope that this post may be helpful to someone in the future! :)

---

