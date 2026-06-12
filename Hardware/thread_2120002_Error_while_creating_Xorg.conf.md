---
title: "Error while creating Xorg.conf"
date: 2013-02-25
forum: Hardware
---

### Post by francoise_peace on 2013-02-25
Xorg error message while creating it:
Ctrl+Alt+F1
```

sudo service lightdm stop
sudo X -configure

```[QUOTE=Xorg]Number of created screens does not match number of detected devices.
Configuration failed.
ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.[/QUOTE]

Xorg.conf was created, looks OK. Just changed one small thing, added "sna".

---

