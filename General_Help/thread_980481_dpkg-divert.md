---
title: "dpkg-divert"
date: 2008-11-12
forum: General Help
---

### Post by High Roller on 2008-11-12
I've made some tweaks to two files on my computer that I want to persist even when an upgrade to the package they belong to occurs.  Would the following commands achieve my goal?

```
sudo dpkg-divert --add /usr/share/nautilus/ui/nautilus-desktop-icon-view-ui.xml
sudo dpkg-divert --add /usr/share/gdm/themes/Human/Human.xml
```

---

