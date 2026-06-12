---
title: "Remotely starting applications on running X sessions"
date: 2008-08-29
forum: General Help
---

### Post by nehsa on 2008-08-29
I have xubuntu set to automatically bring up gdm when I start my machine.  Regardless of whether I'm logged in or not I want to start Pidgin on that X session.  Mainly because I use vnc4server at work.

What I'd like to do is killall pidgin sessions currently open when starting the vnc server.  Then, after my VNC session is finished restart pidgin on the main display.

Here's what my xstartup looks like:
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

## Kill Pidgin on main machine and restart for vnc session
killall pidgin &
pidgin &

fluxbox

##Restart Pidgin on main machine
killall pidgin &
pidgin --display=:0 &


The first part works:
user@server:~$ vncserver :1

New 'server:1 (user)' desktop is server:1

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/server:1.log

nehsa@serverass3200:~$ ps aux | grep pidgin
nehsa     6094  9.3  0.8 355028 25544 pts/0    Sl   09:34   0:00 pidgin
nehsa     6128  0.0  0.0   5164   836 pts/0    S+   09:34   0:00 grep pidgin


This is even before I vncviewer.  When I do, pidgin is sitting there perfectly.  

The problem is with these lines:
##Restart Pidgin on main machine
killall pidgin &
pidgin --display=:0 &

I want Pidgin to restart on the current X session when I quit VNC.  

Even running pidgin --display=:0 with VNC out of the picture doesn't work through:

user@server:~$ pidgin --display=:0
No protocol specified

(pidgin:6130): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Pidgin 2.4.1

** (pidgin:6130): WARNING **: cannot open display: unset

Thanks for any help!

-nehsa

---

### Post by inteluser on 2008-08-29
I get the same error you got with :0, but I got this working with 
pidgin --display=:0.0

(which is to say, just running pidgin on an X server from a virtual console - I'm not using xVnc, but it seems like this shouldn't be an issue.)

---

