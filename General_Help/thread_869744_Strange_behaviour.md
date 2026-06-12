---
title: "Strange behaviour?"
date: 2008-07-25
forum: General Help
---

### Post by mkquist on 2008-07-25
hey peeps, had some interesting things going on in the last day or so.  Click on minimize and gnome restarts.  Tonight a video just started playing out of the blue while I'm not in the room and doesn't show itself as an active window.  Had to go into system monitor to find and kill it... any thoughts?  Also had problems with firefox search... errors are as follows:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:()
9:CM_initMenu([object XULElement],[object XULElement])
10:nsContextMenu([object XULElement],[object XULElement])
11:onpopupshowing([object MouseEvent])

BTW the smileys are not mine.  Just pasted the error.

What is going on?

Any help would be, of course, appreciated.

---

### Post by cyclobs on 2008-07-25
> **mkquist said:**
> hey peeps, had some interesting things going on in the last day or so.  Click on minimize and gnome restarts.  Tonight a video just started playing out of the blue while I'm not in the room and doesn't show itself as an active window.  Had to go into system monitor to find and kill it... any thoughts?  Also had problems with firefox search... errors are as follows:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:()
9:CM_initMenu([object XULElement],[object XULElement])
10:nsContextMenu([object XULElement],[object XULElement])
11:onpopupshowing([object MouseEvent])

BTW the smileys are not mine.  Just pasted the error.

What is going on?

Any help would be, of course, appreciated.


looks to me that there is a file missing some where,

have you got any remote connection enabled or something there?

---

### Post by mkquist on 2008-07-25
The only thing I have going on is Bit Torrent.  Azureus has been running.  Could that have something to do with it?  Running a router and that is the only port open for this machine.  So that Azureus can run correctly.

---

### Post by sysadmn62 on 2008-07-25
I had the same thing happen, but with Firefox.  Restarting firefox did not help, but I rebooted and the problem went away.

Do you have auto-update on?  I do not, and the last thing I did before the problem started was an update  that included:
firefox-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
firefox_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_all.deb
firefox-3.0-gnome-support_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
firefox-3.0_3.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2_i386.deb
cairo-dock_1.6.1.2_all.deb
cairo-dock-plug-ins_1.6.1.2_all.deb
mozilla-thunderbird-dev_2.0.0.16+nobinonly-0ubuntu0.8.04.1_all.deb
mozilla-thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_all.deb
thunderbird-gnome-support_2.0.0.16+nobinonly-0ubuntu0.8.04.1_i386.deb
thunderbird-dev_2.0.0.16+nobinonly-0ubuntu0.8.04.1_i386.deb
thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_i386.deb


xulrunner looks suspicious...  Perhaps this update should have had the system restart required flag?

Again, try rebooting.

---

### Post by mkvnmtr on 2008-07-25
I am not sure if this will help your problem. I always watch the updates through the terminal. The other day it told me that I needed to restart Firefox before it finished or I would have problems. I restarted Firefox and encountered no problems. I wouldn't have seen it if I was not trying to get used to the terminal.

---

