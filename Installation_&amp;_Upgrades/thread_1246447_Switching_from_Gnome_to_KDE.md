---
title: "Switching from Gnome to KDE"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by subnet_rx on 2009-08-21
I have just used aptitude to install KDE along with what I already had which was Gnome.  My problem is, if I try to login on a KDE session, it will not take my user name (and it's the administrator account).  The screen seems to refresh, then login fails.  If I switch the session to Gnome, I can login as usual.  What do I need to do to get KDE to recognize my admin account?

---

### Post by starcraft.man on 2009-08-21
Nothing extra is required in my experience, there is no need to set up accounts for use with KDE. Did you simply install the kde package? If so, I suggest ya go back to apt and install the **kubuntu-desktop** package, that will get ya the full suite of apps. Perhaps something didn't install that's needed? Otherwise, it's an odd problem, like I said, there's no extra step, ya just try and login with whatever DE ya want. If that doesn't work, reply back and well try and narrow this down a bit more.

---

### Post by subnet_rx on 2009-08-21
Yeah, I did a sudo aptitude kubuntu-desktop install.  All the apps are there, but I can't login.

---

### Post by starcraft.man on 2009-08-21
> **subnet_rx said:**
> Yeah, I did a sudo aptitude kubuntu-desktop install.  All the apps are there, but I can't login.

Only thing I can think of is that something went wrong with your user account.

Log into GNOME, then open run command box (alt + f2) then type in **kuser** and return. That's KDEs user management gui, scroll to around the bottom, verify that the account isn't disabled or otherwise not functioning right. Check groups for it as well. There isn't anything really to do, quite an odd problem.

---

### Post by subnet_rx on 2009-08-24
Thanks starcraft.man, I ran kuser and saw no problems.  Oddly enough though, after doing that, I restarted and tried KDE again.  This time it logged in with no problems.  It appears that it was all in vain anyway though, since it seems that KDE doesn't have the level of multi-monitor support that Gnome has.  I have two monitors through a DVI - 2 VGA splitter.  Gnome sees two monitors, KDE sees two monitors, but only Gnome is able to output something different to each monitor.

---

### Post by starcraft.man on 2009-08-24
Well at least the login issue resolved. Perhaps have a look round options, I'm sure KDE could do it with a bit of looking. Might be best to post another thread and ask, I stick to one monitor for PC so wouldn't know the answer.

---

