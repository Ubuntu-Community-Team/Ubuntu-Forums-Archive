---
title: "Are pkg repositories of expired releases removed?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by tcpip on 2009-05-07
What happens to an old release after expiry? For instance, what happens to v7.10 after April 2009?

I was under the impression that updates (all kinds, bug fixes, security updates, the works) are no longer available from Ubuntu, but the package repositories would themselves be available, letting a user download an install the odd package he needs.

But I am now getting the impression that the package repositories themselves are removed. Is this true? In other words, if I now try to perform an "apt-get install XYZ" for v7.10, the .deb file will not be found on the repository?

(Please, please can we avoid getting into the discussion about "Why the hell do you want to use an 18-month-old release anyway?" :) )

---

### Post by HyRax on 2009-05-07
Once a release is no longer supported, there would be little point in keeping the repositories up - after all, they're taking huge amounts of space.

I can appreciate if the official Ubuntu repo servers keep the no-longer-maintained repositories there for awhile longer after expiry, but I wouldn't expect them to keep it long.

All the local mirrors I use (and my own mirror), delete the non-supported releases right away.

7.10 is very old. There is no need to keep using it - upgrade to a more recent release. You'll be far better off for it.

---

### Post by tcpip on 2009-05-08
> **HyRax said:**
> Once a release is no longer supported, there would be little point in keeping the repositories up - after all, they're taking huge amounts of space.

I can appreciate if the official Ubuntu repo servers keep the no-longer-maintained repositories there for awhile longer after expiry, but I wouldn't expect them to keep it long.

All the local mirrors I use (and my own mirror), delete the non-supported releases right away.

Thanks a lot. This clarifies a misconception I and a lot of my Ubuntu-using friends had about what "expiry" means.

> 7.10 is very old. There is no need to keep using it - upgrade to a more recent release. You'll be far better off for it.This is the kind of advice I don't need. I'd like to hand over my laptop (a Thinkpad X60s) to you and see you get even basic X working on it with 8.04 and 8.10. :)

No offence intended, but I've been working with Linux since the kernel 1.0.8 and Slackware (year: 1994). I too would like to upgrade to the latest releases whenever possible, but when I don't, it's because I'm really irritated by how old mainstream functionality is broken in newer releases.

---

### Post by amac777 on 2009-05-08
After the support period for a version ends, the repositories for the expired version are moved here:

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

If you need to keep using an old release, you can update your /etc/apt/sources.list to point to the above server and that will allow you to still install programs using apt-get and synaptic. Of course, there will be no updates or security fixes to the old-releases, but at least they are there if you need to keep running them for some reason.

---

### Post by HyRax on 2009-05-08
> **tcpip said:**
> 
This is the kind of advice I don't need. I'd like to hand over my laptop (a Thinkpad X60s) to you and see you get even basic X working on it with 8.04 and 8.10. :)

I probably wouldn't try. I'd stick DSL or something on instead. That's what I did with my old Compaq Armada. It only has a 4GB HDD and 64MB RAM which can run X, but very few decent window managers! Actually when I think about it, I think I've got Arch on there right now, not that it's actually doing anything useful atm...

> **tcpip said:**
> 
No offence intended, but I've been working with Linux since the kernel 1.0.8 and Slackware (year: 1994). I too would like to upgrade to the latest releases whenever possible, but when I don't, it's because I'm really irritated by how old mainstream functionality is broken in newer releases.

Each to their own. Personally while I'm not a fan of everything that changes either, I know it can be ultimately for the Greater Good(TM) that it does! :D

---

### Post by tcpip on 2009-05-08
> **amac777 said:**
> After the support period for a version ends, the repositories for the expired version are moved here:

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

If you need to keep using an old release, you can update your /etc/apt/sources.list to point to the above server...

Thanks a million. You've made my day ... nay, week. :D

Actually, this is what I was hoping the Ubuntu team would be doing. I'm sorry I couldn't find it documented anywhere, I guess it's my limited searching ability.

---

