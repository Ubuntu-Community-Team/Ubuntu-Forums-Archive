---
title: "Removal of old files"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2009-02-23
Does Linux removes all unnecessary files after an installation, removal, upgrade or update?

---

### Post by snova on 2009-02-23
> **xtiano77 said:**
> Does Linux removes all unnecessary files after an installation, removal, upgrade or update?

I suppose it depends on how you define "unnecessary". I can't think of anything in particular, though except:

1) Configuration files. These are left by default when you remove a package, unless you explicitly purge them (apt-get purge <package>).

Also, there is nothing to remove per-user configuration files.

2) The packages themselves are cached, but I don't think that counts... if you want those removed, it's:

```
apt-get clean
```

Beyond that, I can't think of anything.

---

### Post by UbuntuNerd on 2009-02-23
you need to install localepurge. This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.
also check this [GUIDE](http://my.opera.com/ubuntunerd1/blog/2008/12/26/keeping-ubuntu-clean)

---

