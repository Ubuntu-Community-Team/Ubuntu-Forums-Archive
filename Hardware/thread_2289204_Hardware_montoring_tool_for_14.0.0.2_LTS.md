---
title: "Hardware montoring tool for 14.0.0.2 LTS"
date: 2015-08-02
forum: Hardware
---

### Post by mchain on 2015-08-02
Already have a monitoring tool for windows.  Installed lm-sensors but that asked for root when sensors command was run?

Closest thing found here with forum search here, but this post is from 2009:  [URL="http://ubuntuforums.org/showthread.php?t=1264138&highlight=hardware+monitoring+tool"]http://ubuntuforums.org/showthread.php?t=1264138&highlight=hardware+monitoring+tool




[/URL]

---

### Post by tgalati4 on 2015-08-02
You need to run *sensors-detect* as root.  It may install modules (hardware drivers) in your /etc/modules file.  Reboot then run the *sensors* command to see if any additional sensors are detected.  If they are, then you can display them on your panel using a hardware monitoring applet.

```
sudo sensors-detect
```

---

