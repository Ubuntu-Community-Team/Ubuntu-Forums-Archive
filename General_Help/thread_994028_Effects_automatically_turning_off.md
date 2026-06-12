---
title: "Effects automatically turning off"
date: 2008-11-26
forum: General Help
---

### Post by AZorin on 2008-11-26
Hi I got this weird problem, the desktop effects keep turning off by themselves can anyone plz help (I also checked compiz-check it says it is OK)

---

### Post by stormtrooprdave on 2008-11-26
same thing as this thread

[http://ubuntuforums.org/showthread.php?t=991663]("http://ubuntuforums.org/showthread.php?t=991663")

I think the compiz updates have ballsed it up

---

### Post by damis648 on 2008-11-26
> **stormtrooprdave said:**
> same thing as this thread

[http://ubuntuforums.org/showthread.php?t=991663]("http://ubuntuforums.org/showthread.php?t=991663")

I think the compiz updates have ballsed it up

Yes, it is an update issue. See this thread:
[http://ubuntuforums.org/showthread.php?t=990349](http://ubuntuforums.org/showthread.php?t=990349)

All i did was purge compiz:
```
sudo apt-get --purge compiz compiz-core compiz-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf compizconfig-settings-manager emerald
```

(I was using the PPA's so I disabled those but you probably do not need to worry about that)

and then reinstalled:
```
sudo apt-get install compiz compiz-core compiz-dev compiz-fusion-bcop compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf compizconfig-settings-manager emerald
```

and that fixed it.

---

### Post by AZorin on 2008-12-03
4 Me it said ```
E: Invalid operation compiz

``` any other way?

---

