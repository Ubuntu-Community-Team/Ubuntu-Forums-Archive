---
title: "Dual-boot with Openoffice.org problem"
date: 2005-11-17
forum: General Help
---

### Post by dfourth on 2005-11-17
I dual boot Ubuntu Hoary with XP, running Openoffice.org on both.  Until the recent release of V2.0, both operating systems ran the same version of Openoffice, and I had no compatibility issues with files.  I routinely work with the same file from either operating system, but that suddenly came to a halt with the upgrade to 2.0 in XP.  Once upgraded in XP, opendocument files that I edited in XP were not usable in Ubuntu.  Attempting to load them caused Openoffice to lock up, and sometimes continue to use 100% CPU even after force quit, requiring a process kill.  I have only seen this with the (new) opendocument format.  I can read the older format and .doc formats without a problem.  I followed the post for upgrading Ubuntu Openoffice to 2.0, which appeared to be successful, but suffered the same complaint as the older version.  I eventually stripped that out and returned to the official release, as it appeared to be unstable on my system.  I also should mention that I have Kubuntu installed as well, and verified the same result in both KDE and Gnome.  Has anyone else experienced problem reading/writing the same file in XP and Ubuntu?

---

### Post by elempoimen on 2005-11-17
enable the following repository in synaptic and install OO.o2

[http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by dfourth on 2005-11-18
That method didn't work for me.  I tried it again, and got the same response.  Synaptic won't upgrade the package using Smart Upgrada, and tyring to select the openoffic.org2 metapackage for upgrad results in numerous dependency issues that can't be resolved, so again, no upgrade.  I'm also rather irritated that Synaptic won't let me edit repositories.  Instead, I have to edit /etc/apt/sources.list directly.  Clicking on 'repositories' in the Synaptic menu just caused an automatic reload.

---

