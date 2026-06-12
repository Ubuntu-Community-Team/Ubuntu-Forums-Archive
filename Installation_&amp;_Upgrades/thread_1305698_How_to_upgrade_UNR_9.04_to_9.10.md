---
title: "How to upgrade UNR 9.04 to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by blwizard on 2009-10-30
I have read the upgrade instructions but I can't seem to upgrade from my UNR9.04.

I tried updating all existing software and hitting "check" again, but no matter how many times I click on it, it always says my system is up-to-date.

What's going on?

---

### Post by kfaughnan on 2009-10-30
Hi blwizard,

You need to run your update manager with the -d switch.

So hit Alt-F2 and enter ```
update-manager -d
``` into the box that pops up. When update manager opens it should tell you theres an upgrade available.

Killian

---

