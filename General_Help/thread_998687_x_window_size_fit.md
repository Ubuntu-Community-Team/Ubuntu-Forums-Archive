---
title: "x window size fit"
date: 2008-12-01
forum: General Help
---

### Post by candidoaramburu on 2008-12-01
Hi,

I have installed on pentium III, 124Mb RAM:

1- ubuntu 8.04 console mode
2- sudo aptitude install xorg
3- sudo aptitude install fluxbox fluxconf
4- sudo aptitude install idesk
4- sudo aptitude install xdm

I have customize ~/.xsession shell script

#!/bin/sh
idesk &
exec fluxbox

After login in the fluxbox window manager correctly i execute an aplication ( squeak ). This application dont fit correctly the window wrapper because the MENU BAR is HIDE from window bounces. The scale of this applications is not correct.
The scale of fluxbox desktop menus is correct. 

I have try scale it changing the /etc/X11/xdm/Xservers configuration file with the -dpi option but the error continue.

How can i control the size scale of the window application? Its the x server who control it, or login manager xdm or window manager fluxbox or its a problem of the aplication.

I have installed this application in others machines with the same architecture machines and the problem is only in this one.

THANKS

THANKS

---

### Post by hictio on 2008-12-01
You might want to try passing a "--geometry" value to the startup parameters of Squeak?
Like this xterm example:

```

xterm -title Tesla -fn 9x15 -geometry 106x28-10+182

```

Take a look at this thread [gnome-terminal windows size on open](http://ubuntuforums.org/showthread.php?t=991037)

---

