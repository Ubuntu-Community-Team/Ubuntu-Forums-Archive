---
title: "upgrade to 8.04 gone wrong"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by jmartrican on 2009-01-30
hello,

I'm normally a cli so I didn't notice that I had an ongoing issue with my desktop on gutsy.  After a few minutes of using the desktop, it would lock up (I could move the mouse but everything else was unresponsive).  CLI still works though if I log in remotely.  

So I tried upgrading to heron via the desktop knowing that the possibility of locking up during install was there (if i do not touch the mouse i figured it might not happen).  After the upgrade procedure downloaded all the file and started the install then the questions started.  Sure enough while clicking on one of the answers the desktop locks up.  I did not know how to restart the desktop so i restarted the computer.

Now the desktop allows me to login and move the mouse, but no taskbar or background pic shows up.

I figure my choices are to find a way to continue (or restart) the upgrade over CLI or fix the desktop issue.  The comp still boots up with gutsy.  Any suggestions on what I should do and maybe how I would go about it?

thanks!

---

### Post by jmartrican on 2009-01-30
I did a 

dpkg --configure -a

as requested by apt-get.  It looks like that is causing the upgrade to finish.  I'll respond with the results in case anyone is holding their breathe in anticipation.

---

### Post by hansdown on 2009-01-30
Hope it goes well jmartrican.

A fresh install is another option.

---

### Post by jmartrican on 2009-01-31
Everything seems fine now.  It was very cool to see that ubuntu was able to finish off where it last left off at after being restarted.

---

