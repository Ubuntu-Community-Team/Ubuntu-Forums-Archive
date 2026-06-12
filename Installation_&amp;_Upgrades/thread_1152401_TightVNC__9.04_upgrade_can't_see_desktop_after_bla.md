---
title: "TightVNC  9.04 upgrade: can't see desktop after blank screensaver activates"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by oldtappan on 2009-05-07
I have my screensaver to set to a blank screen with password.  When connected to my 9.04 box, after the screensaver activates, all I see is my mouse pointer against a black desktop.  Moving the mouse or pressing keys doesn't light anything up.  I can't see the password dialog or the screen or anything else.  Disconnecting and reconnecting doesn't help.  

This was working before I upgraded.  I'm using TightVNC Server 1.3.9.  Help.

---

### Post by rollback on 2009-08-21
anyone?  i have the same problem.  

i've read elsewhere that it needs to run as a service, but stopped short of explaining why or how in ubuntu.  

here is my service script: 

/etc/init.d/vncserver

[FONT=Courier New][COLOR=DarkGreen]#!/bin/sh

USER="joe"
DISPLAY="1"
DEPTH="24"
GEOMETRY="1280x1024"
NAME="vnc-desktop"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"

case "$1" in
start)
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;

stop)
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;

exit 0
[/COLOR][/FONT]

the service script starts vncserver just fine, but after some idle time, the screen will lock, and just stay blank, no prompt for password.

---

### Post by rollback on 2009-09-22
I decided to uncheck the option that locks the screen when the screen saver is active. I can still manually lock the screen whenever I leave my desk. But the vnc session running on 5901 won't lock when it exists the screen saver.

---

