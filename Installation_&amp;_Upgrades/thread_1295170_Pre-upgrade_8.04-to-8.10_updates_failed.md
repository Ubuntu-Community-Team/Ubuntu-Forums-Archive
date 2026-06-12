---
title: "Pre-upgrade 8.04-to-8.10 updates failed"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by frisket on 2009-10-19
I want to upgrade 8.04 to 8.10, so I checked "Normal releases" in Software Sources|Updates, and ran Update Manager, clicked Check, and it said it was downloading updates (1 of 22). So I waited...then it said an error had occured (I'm set to "Server for Ireland" :-)

> W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_IE.bz2)  Unable to connect to ie.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.


So it won't let me update, so I can't upgrade in place. I tried setting Sources to "Main server" and got

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_IE.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_IE.bz2)  Unable to connect to archive.ubuntu.com http: [IP: 91.189.88.31 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

I tried several nearby repos, but they all give similar errors.

Is it still possible to upgrade from 8.04 to 8.10 over the network? Is there a way to selectively disable the i18n stuff? I wanted to do an upgrade-in-place by staes to 9.04, because the installer CDs don't appear to provide any way to preserve existing data, only to wipe the partition. I'd rather try to keep my /home directory; and I also have Windows in another partition as well.

Baffled...

---

### Post by dstew on 2009-10-19
According to [this thread]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/7790") there is a package **anon-proxy** that can give you this error. If anon-proxy is installed, remove it using Synaptic or apt-get (try to remove it completely) and restart, then try again.

---

### Post by frisket on 2009-12-11
> **dstew said:**
> According to [this thread]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/7790") there is a package **anon-proxy** that can give you this error. If anon-proxy is installed, remove it using Synaptic or apt-get (try to remove it completely) and restart, then try again.

Thanks for the idea. Fortunately I found I could wipe and install 9.10 which fixed all the problems.

Never do upgrades: always wipe and install from scratch.

P

---

