---
title: "Logon Screen Display Problem"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by wrp on 2009-06-08
I have just changed to the nVidia proprietary drivers on Ubuntu 8.04 LTS and reset the screen resolution to 1600 x 1200
At logon the top right corner of the regular logon image fills the entire sreen and the username and password dialog boxes are off screen and therefore not visible to the user. 
Everything works - i.e type username (Enter) password (Enter) and login continues as normal but it is quite disconcerting being unable to see what you are typing. 
There must be somewhere to either reset the size of the image back to ??1024 x 768 OR increase the resolution of the sreen at logon so that one can see what one is doing.
Any help appreciated.

---

### Post by wrp on 2009-07-04
Found a solution although it does not appear that elegant.

See 
[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

Edit /etc/X11/xorg.conf
"In the Section “Screen”, SubSection “Display”, you have two entries:
Modes and Virtual.
For the login, X will default to the first resolution defined in the “mode” entry. Thus, you must select the resolution you want (say, “1280×1024@60&#8243;) and move it to the first position."

The annoying part is that the monitor is set to 1600 x 1200 but for some reason ubuntu assumes and uses a lower resolution for the monitor at login but at the same time increases the size of the login screen so that it no longer fits.....

I am sure there is a better fix somewhere.

---

