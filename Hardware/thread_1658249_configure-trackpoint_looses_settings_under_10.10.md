---
title: "configure-trackpoint looses settings under 10.10"
date: 2011-01-02
forum: Hardware
---

### Post by mgw2008 on 2011-01-02
I've installed the configure-trackpoint utility under Kubuntu 10.10 (Maverick) it works fine but the settings are not stored, i.e. after suspend (ACPI state S3) all settings are lost. If I do a system restart the options are loaded... arrgh

---

### Post by Zorael on 2011-01-03
What package is this utility in? I don't see configure-trackpoint in the maverick repositories.

It might be that the utility creates an autostarting script that runs as you log in, reloading your settings, which isn't run when you resume from sleep. In that case you'd have to write a complementary script in **/etc/pm/sleep.d/** that runs that other script.

What files do you have in **~/.config/autostart**, **~/.kde/env** and **~/.kde/Autostart**?

```
$ ls ~/.config/autostart ~/.kde/env ~/.kde/Autostart
```

---

