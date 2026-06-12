---
title: "esd startup problems on thinkpad"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by kadissie on 2005-04-07
Today, on restarting my machine (an IBM Thinkpad 600E) gdm started fine, but when I tried to login I got a desktop background with a (movable) mouse cursor on it and nothing else - no matter how long I waited.

I'm not sure if this problem is due to a recent update; I last updated packages a week ago, but since then I have not fully shutdown the computer (I hibernate instead).

I'm running Hoary and have previously had problems with the onboard sound on this machine (see my previous posts on the forum... :-(  I finally deduced that it was the Enlightenment Sound Daemon (ESD) by systematically killing off processes until the login worked, and I have verified through repeated reboot cycles that killing esd does in fact solve this login problem.

Needless to say, I still have no sound....  But since this machine belongs to a friend who I'm trying to convert to FOSS, a machine that won't let him log in is rather a turn-off.  Anyone have any ideas?

R.

---

### Post by kadissie on 2005-04-11
I've fixed the problem, if anyone cares....

So I said that the sound is not working.  Each user on the system can set sound Preferences through a GUI (System -> Preferences -> Sound, IIRC), and one of the options is "Enable sound at startup", which is ticked by default.  I simply unticked it for each user, and the logins worked fine.

So apparently the problem is that GDM or gnome-session or some login script was trying to start up sound services which didn't exist, and instead of ignoring the problem it just hung.

---

