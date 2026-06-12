---
title: "Why does my laptop ignore low battery?"
date: 2009-11-28
forum: Hardware
---

### Post by ThomasJ02 on 2009-11-28
I have an Acer Aspire One laptop running a fresh Karmic install (not netbook remix). The gnome battery indicator seems to accurately reflect the charge of my battery, but:
1) I don't get any warnings when the battery gets low
2) The laptop powers down hard when it runs out of battery, instead of going into hibernate as it's configured in the "On Battery Power" tab in the Power Management settings.

How can I fix these problems?

---

### Post by nixscripter on 2009-11-28
Check your settings in the Gnome power manager, by right-clicking on the applet icon and selecting Preferences. What are the "On battery Power" tab settings for "when battery power is critically low"?

---

### Post by ThomasJ02 on 2009-11-28
It's set to "Hibernate" for "When battery power is critically low"

---

### Post by nixscripter on 2009-11-29
Looking around, there was apparently a bug in Ubuntu some versions back with it detecting imaginary batteries:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/135548](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/135548)

Open a terminal, and run this to verify that the system thinks there is only one:
```
cat /proc/acpi/battery/*/state
```

---

