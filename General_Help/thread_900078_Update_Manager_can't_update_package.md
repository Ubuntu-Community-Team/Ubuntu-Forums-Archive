---
title: "Update Manager can't update package"
date: 2008-08-25
forum: General Help
---

### Post by niccholaspage on 2008-08-25
I am running Ubuntu 8.04 Hardy on this desktop computer.Now I removed kde4 from it and for some reason this removed virtualbox-ose.I was going to update my system.So I went to the update manager and It said there was an update to virtualbox-ose-modules-generic,Which I don't need.I can't check it or install it or do anything with it.

---

### Post by carolinason on 2008-08-25
If you want to remove virtualbox-ose-modules-generic?
```
sudo aptitude remove virtualbox-ose-modules-generic
```

---

### Post by niccholaspage on 2008-08-25
I'm running gnome.I did run the commands sudo aptitude update and sudo aptitude safe-upgrade but I still see the package in the update manager.

---

### Post by prshah on 2008-08-25
> **niccholaspage said:**
> I'm running gnome.I did run the commands sudo aptitude update and sudo aptitude safe-upgrade but I still see the package in the update manager.

After Sun's takeover of InnoTek, virtualbox-ose has ceased to exist; now there is only one VirtualBox (ver 1.6). It is "free" for personal use. The update you see is related to 1.6 virtual box, so it's listed but unselectable.

You may have a repository listed in "/etc/apt/sources.list" from where this is being picked up. Edit the file and comment out any related repository. If you cannot find such a line, post the sources.list file here, and someone can advise you.

---

