---
title: "White Screen of Death"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by dealcorn on 2009-11-10
Upon a fresh jaunty install caused by an emergency motherboard replacement, login looks good and I get good sound after entering my password but I am dumped to an unresponsive white screen with nowhere to go.  Karmic install works great but there are unrelated application issues.

The m/b has an Intel G41 chipset (ESC Elitegroup G-41T-M) and while locally available was not my preferred choice.  ALT F2 does nothing.  How should I proceed?

---

### Post by dealcorn on 2009-11-11
the command:

```
sudo aptitude safe-upgrade

```
fixed much of the problem.  Now I boot to a command line from which I currently execute startx and then some combination of ALT F2 a couple times with other wild guesses gets me to a display I can work with.

What is the actual correct command to bring up the desktop?  Where should I look for guidance on how to correct my configuration?

---

### Post by MichealH on 2009-11-11
CTRL-ALT-F7

LOL the BSOD has a Linux brother the WSOD

---

### Post by dealcorn on 2009-11-11
With the benefit of hindsight and a fresh install, the exact steps required to eliminate my white screen problem from the recovery boot console are:
```
sudo aptitude update
sudo aptitude safe-upgrade
```

Then, select the "try to fix graphics drivers" option within the recovery boot option.  For me these 3 steps appear to be a complete fix.  Aptitude requires Internet access so you may also need to configure your wireless adapter.

---

### Post by fela on 2009-11-11
> **MichealH said:**
> CTRL-ALT-F7

LOL the BSOD has a Linux brother the WSOD

Except the WSOD is easily fixable by going to a tty and killing the rogue application (e.g. compiz). A bsod in Windows requires a restart, hosing all your unsaved data. Just a thought.

---

