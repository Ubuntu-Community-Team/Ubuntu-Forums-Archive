---
title: "Reinstall XORG?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by funnyav on 2009-07-11
How is this done? Not the config, the entire thing.

Thanks

---

### Post by akudewan on 2009-07-11
The command for reinstalling a package is 
[CODE]
sudo apt-get install --reinstall [packagename]
[CODE]

In your case [packagename] would be xorg.

I'm not sure if existing configuration files will be purged.

---

