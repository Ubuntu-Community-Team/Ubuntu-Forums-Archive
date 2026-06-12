---
title: "gnome settings daemon broken on upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by nospoon on 2009-04-24
I upgraded via update-manager from fully updated 8.10 to 9.04, and following, applications relying on gnome-settings daemon stopped working.  Preference apps like "sound" and "appearance" don't load properly, and themes are not properly applied.  

When I try to start gnome-settings-daemon via the command line I get this error:

 ```
 $gnome-settings-daemon

** (gnome-settings-daemon:30850): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:30850): WARNING **: Could not acquire name

```

Any help would be greatly appreciated.

---

### Post by stco on 2009-04-29
I had the same problem yesterday.

In my case, I noticed that in synaptic the package gstreamer0.10-plugins-ugly was not updated to the last version, I updated it to the version 0.10.10.2-1build1, rebooted and this solved the problem.

Hope it helps!

---

