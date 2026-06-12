---
title: "Autostart xfce4"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by richardjc on 2009-01-07
**To autostart on xfce4 (Xubuntu)**

create a .desktop file in the /etc/xdg/autostart folder. call it "autostart.desktop" for example

**inside the .desktop file put:**

```
[Desktop Entry]
Type=Application
Name=Name of Your App
GenericName=What you call your App
Comment=
Exec=the command to run your App
Icon=location for the icon image of App
Terminal=false
Categories=Application;Utility;
StartupNotify=false
```

**you can also check this link on creating a .desktop file**
[http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en")

---

