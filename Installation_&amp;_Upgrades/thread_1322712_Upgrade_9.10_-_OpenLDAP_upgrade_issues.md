---
title: "Upgrade 9.10 - OpenLDAP upgrade issues?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by lil_elvis2000 on 2009-11-11
I currently have a server on 9.04 which is my OpenLDAP server, runs a Samba domain and authentication for Linux as well as internal websites.

Are there any known issues with the upgrade to 9.10 for OpenLDAP. I can't seem to find any release notes on this. When I upgraded from 8.10 to 9.04 I had to reload and reconfigure the OpenLDAP. Do I need to do that again?

Its really a pain having to rebuild it each time. Can someone point me to the release notes for 9.10 - especially regarding OpenLDAP upgrade.

Thanks

---

### Post by apedraza on 2009-11-12
Don't do it!!!!!  Huge issues.. I wish I had not updated.  Stay with Jaunty until all is clear.  

The update inserts undocumented (and unwanted) directives in  your cn=config and other databases.  I am still trying to debug this after a week...

My syncrepl stopped working properly...

---

### Post by lil_elvis2000 on 2009-11-13
Thanks, I knew there had to be something. Last set of release notes for 9.04 also didn't mention anything about OpenLDAP update either. And when I did it, my OpenLDAP was broken. Only laster by hunting around did I find that this was an issue.

If I was to backup all my config files and then remove OpenLDAP, then perform the upgrade, install OpenLDAP and overwrite the config files then restore from my slapcat'd backup files. Would that work?

Anybody....though my gut tells me to wait for Lucid.

---

### Post by lil_elvis2000 on 2009-12-04
thought i'd just bump this

---

