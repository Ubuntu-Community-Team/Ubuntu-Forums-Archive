---
title: "Update manager stops checking for updates in Jaunty after resume from suspend"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by bedhead75 on 2009-06-23
Has anyone else noticed this problem?  I have set the update manager to check for updates daily, but I consistantly notice that I never get notified of new updates or security fixes until I do a complete reboot of the system or until I check for updates manually.  When I finally do this, I see a long list of updates and fixes that I've missed for weeks it seems.  Usually I just put my computer to suspend (works flawlessly for me in Jaunty now) at night instead of turning it off, and it's as if my system thinks it's still the same day as before when I resume, so it doesn't bother checking for updates anymore.  This might be a security issue too if users are not being made aware of security fixes the moment they come out.

---

### Post by mk1w86 on 2009-06-24
I think this happens because when you reboot the machine the package lists get updated whereas when you suspend and resume they do not.

---

### Post by bedhead75 on 2009-06-25
Hmm...interesting.  Can anyone confirm this?  If what you say is true, then it would mean that the package list gets updated only after every time you boot.  This implies that if you left your system on 24/7, it would only check for updates once, and you'd have to manually check for updates afterwards.  This can't be right because if you set your package manager to check for updates daily, doesn't it do so automatically when you leave your system on all the time?  I've noticed this doesn't happen anymore once you resume from a suspended session.

---

### Post by dsavi on 2009-06-25
No, that can't be true, it just doesn't make sense. It would have been come across long ago if that were the case.

---

### Post by mk1w86 on 2009-06-26
There is another thread here about problems with automatic update checks in Jaunty.

[http://ubuntuforums.org/showthread.php?p=7520201#post7520201](http://ubuntuforums.org/showthread.php?p=7520201#post7520201)

I don't know if any of it is relevant to your problem bedhead75. :?

---

### Post by mtb-cliff on 2009-07-05
Yeah, I have the same problem on all four of my jaunty systems. I don't know if it work when you reboot or not, as the systems are usually just sleeping instead of shutdown.

---

