---
title: "Deleted Stuff out sessions preferences"
date: 2008-07-23
forum: General Help
---

### Post by linuxology on 2008-07-23
I deleted some things out of sessions instead of unchecking them.  Can you tell me how to get them back in there.  These are the startup programs for Ubuntu.  Everything works fine, but I would like to add them back.  They are:

Bluetooth Manager
Check for New Hardware Drivers

To get to sessions you go to System>>Preferences>>Sessions

---

### Post by drs305 on 2008-07-23
From there, just add them back. I deleted bluetooth but the command for Check for New Hardware Drivers is:
```
jockey-gtk --check 60
```

---

### Post by Tim Sharitt on 2008-07-23
Bluetooth Manager is
```
bluetooth-applet --singleton
```

---

