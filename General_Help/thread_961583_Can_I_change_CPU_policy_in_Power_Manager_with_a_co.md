---
title: "Can I change CPU policy in Power Manager with a command?"
date: 2008-10-28
forum: General Help
---

### Post by NotMarkus on 2008-10-28
I've been searching for a while for a way to switch the CPU policy (Dynamic, Performance, or Powersave) on my EEE PC with Kubuntu Hardy. Ultimately I'd like to be able to use either a keyboard shortcut (ie. Super+1, 2, or 3) or just run the command from Katapult--thus eliminating any touchpad usage to change power scaling.

However, at the moment, using guidance-power-manager, the only way to switch is to right click the tray icon, go to CPU Policy, and select one of the options. Is there any command I could run in the terminal that would switch these, if not with guidance-power-manager, then could it be done with another app?

Thanks

---

### Post by bobyy on 2008-10-28
Ciao

So you can run from command line

$sudo cpufreq-set -g powersave (ondemand , performance , conservative)

this will change your cpu policy
or you can create aliases in .bashrc for this

---

### Post by NotMarkus on 2008-11-02
Awesome. Thanks!

---

