---
title: "after upgrade, firefox64 resolves names, firefox32 doesn't"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by JohnAspinall on 2009-09-09
[ x86_64 thinkpad 4GB ]
I just did the 7.10 -> 8.04 upgrade.  Kudos to the upgrade manager - most things seem to be just fine.  Now the problem:

In an attempt to debug browser plugins, I ran 64bit firefox and 32bit firefox side by side.  firefox64 is able to resolve domain names, firefox32 isn't able to get name resolution.  firefox32 can connect to the network - I can connect to [http://192.168.1.1/](http://192.168.1.1/) e.g. but it can't get anywhere by name.

What on earth could be causing this?
Additional clue: a java web start application also fails to do domain name resolution.

---

### Post by JohnAspinall on 2009-09-09
And in case it wasn't clear, javaws (Java Web Start) is also a 32bit app.

---

### Post by JohnAspinall on 2009-09-10
And the solution is installing the lib32nss-mdns package, which apparently got missed during dependency analysis.

---

