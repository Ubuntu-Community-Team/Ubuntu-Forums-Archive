---
title: "bug? - where'd the Update icon go?"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2009-08-08
In Hardy, updates arrived with an icon in the menubar.  In Jaunty, that doesn't seem to be there anymore?  Is there a setting somewhere to turn that behavior back on?

---

### Post by Revolutionary101 on 2009-08-08
Open Update Manager and click on Settings. Another window should pop up and under the section Automatic Updates click "Only Notify me about available updates". That should fix your problem.

---

### Post by drs305 on 2009-08-08
If you want to put the icon back on the panel instead of having a notification window pop up:
```

gconftool-2 -s --type bool /apps/update-notifier/auto_launch false

```
It will still check for normal updates once a week, with security updates available immediately. To change the frequency, open gconf-editor and change the settings:
```

gconf-editor /apps/update-notifier/

```

---

