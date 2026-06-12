---
title: "A &quot;very bad or inconsistent state&quot;"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by superbiskit on 2009-10-16
During a net-upgrade of Karmic, something broke leaving package [BOLD]likewise-open5-eventlog[/BOLD] in a state such that APT (actually, I think, DPKG) complains it is in a "very bad or inconsistent staate.  You should reinstall it before trying to ..."

Re-install doesn't work.  At this point I believe my best bet is to totally purge it.  But, I must do that manually, it seems.  

I've moved the related files from [BOLD]/var/lib/dpkg/info/[/BOLD].

Is that enough?  Do I need to go through [BOLD]likewise-open5-eventlog.list[/BOLD] and remove the regular files it lists?  Do I need to do something to convince dpkg that it's gone?

---

