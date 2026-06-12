---
title: "clean package remove"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by houcem on 2009-04-03
How to remove a package, all unused dependencies and all preferences and config files that it created in only one command? When I use dpkg --purge hidden config files or folders (containing plugins...) always remain in ~!

---

### Post by spcwingo on 2009-04-03
For example say you wanted to remove vlc, all orphaned dependencies, and config files run:

```
sudo apt-get remove --purge vlc && sudo apt-get autoremove && sudo rm -rf ~/.vlc
```

WARNING:  Please be sure you enter the config folder location correctly.  The command "sudo rm -rf" is very powerful and has the potential to destroy your install as well as everything else on the HDD.

---

### Post by sheshbesh on 2009-04-03
You may want to look into using aptitude, that takes care of removing unnecessary dependencies automatically:
```
sudo aptitude purge package_name
```
or the tricky:
```
sudo aptitude install package_name_
```
where the _ following the package name overrides the install command and tells aptitude to purge it (=remove+remove config files)
(I, myself, prefer using the lower-level apt-get as indicated in post #2)

---

### Post by snova on 2009-04-03
> **houcem said:**
> How to remove a package, all unused dependencies and all preferences and config files that it created in only one command? When I use dpkg --purge hidden config files or folders (containing plugins...) always remain in ~!

How to remove the dependencies and system-wide configuration files has already been covered, but I don't think there's anything you can do about user-specific files (at least not through dpkg/apt-get/others), because the package manager will never touch your home directory.

---

