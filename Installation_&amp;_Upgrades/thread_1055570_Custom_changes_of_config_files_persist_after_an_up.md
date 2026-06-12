---
title: "Custom changes of config files persist after an upgrade ?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Devport on 2009-01-30
When a system config file, e.g. /etc/nanorc, was changed by user what happens when the respective package is being upgraded ?

1. Will the config file be overwritten with the new one, dismissing any user applied changes ?
2. Will the config file not be updated at all dismissing any updates to the config file ?
3. Will the custom changes be detected and applied to the new one  ?

I suppose that ubuntu / debian / apt will do either 1 or 2 which both will lead to data loss.

The third solution is the smartest and is used on gentoo -  changes will be detected and automatically applied to updates of config files. If the changes cannot be applied automatically the admin will be able to see which changes werent made and can then apply them manually ( e.g. using meld ).

Is there a way on ubuntu to find out if there were conflicts and is it possible to update those files manually using meld ?

---

### Post by lemming465 on 2009-02-01
As best I understand it, for each config file conflict, the installer will prompt you for a choice of 1 or 2, or dropping to a shell to play with things yourself. If you have "meld" installed it would probably be available to use.  I don't think the debian and ubuntu installers are yet smart enough to either prompt entirely in advance, or to save copies of the files the way RPM-based installers do.

---

