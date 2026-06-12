---
title: "NON-GUI turning monitor off automatically"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by Coldmiser487 on 2007-03-14
I am looking for a way to turn my monitor off automatically while on the login window or on a non-gui virtual desktop.

I have it setup to turn off automatically in X _[COLOR="RoyalBlue"][from this thread]("http://www.ubuntuforums.org/showthread.php?t=381955")[/COLOR]_ , but unfortunately, it does not turn off automatically when it's not in X.

Does anyone know how I can set a command line 'screen saver' to turn my monitor off automatically in runlevel 3 (well, I use runlevel 5, but I do switch to full screen shell virtual desktops).

---

### Post by Coldmiser487 on 2007-03-16
:bump:

---

### Post by mr.v. on 2007-04-07
hey...sorry for the late reply but maybe you're still interested. (ran into this thread accidentally on google). At least in Slackware, there's a program called **setterm**. Ubuntu *should* have it. I haven't run Ubuntu in a bit though. Anyway, look for /bin/setterm and the setterm man page.

Basic usage for what you're talking about is to add the following line to one of your rc scripts. I have mine in /etc/rc.d/rc.M

the line is as follows:
/bin/setterm -blank 15 -powersave powerdown -powerdown 60
that will cause the screen to turn black in 15 minutes (but not suspend). Monitor standby will occur at 60 minutes...

Hope this helps.

---

