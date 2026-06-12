---
title: "apt-get and PHP 5.3"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by jahservant on 2009-10-21
I don't know how much of a noob question this is, but I'm very curious as to how and when packages become available via utilities like apt-get.

Specifically, I'd like to utilize some of the new features in PHP 5.3.0, which is now released, but apt-get recognizes PHP 5.2.x as the latest version.

True, I could download and install from source, but I don't trust myself doing that (especially on a live server).

Perhaps there is a release plan somewhere for apt-get that I could look it up on?

I'm running ubuntu server; I doubt that makes a difference but thought I'd put it out there anyway....

---

### Post by slakkie on 2009-10-21
php5.3 is released, then you need to wait a bit, because once Ubuntu is released it will not do major updates on packages.

Think it is a safe bet 5.3.x will be in the 10.04 version of Ubuntu. Karmic runs 5.2.10.

5.3 is currently in Debian experimental, so hopefully be moved to unstable soonish. Then it will be included in 10.04 once Ubuntu syncs with Debian unstable.

Another way is to find a PPA which has PHP 5.3.x

---

