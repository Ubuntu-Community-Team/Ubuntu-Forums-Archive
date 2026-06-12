---
title: "Run levels?"
date: 2005-11-25
forum: General Help
---

### Post by wunderbar on 2005-11-25
Hi.  I'd like to setup ubuntu to not start x at every boot.  I tried editing the /etc/inittab file, but I noticed that it defaults to run level 2.

Ubuntu's run levels are confusing me.  In most other linux distro's I've tried, run level 5 should be multi-user with X, level 3 should be multi-user no X.

if someone could help me out with this that would be great.

I'm running 5.10 btw.

---

### Post by speedman on 2005-11-25
update-rc.d -f gdm remove


Regards,

SM

---

