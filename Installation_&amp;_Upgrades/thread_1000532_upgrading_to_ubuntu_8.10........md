---
title: "upgrading to ubuntu 8.10......."
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by abhilashm86 on 2008-12-03
can we upgrade ubuntu 8.04 to 8.10 using terminal,can any1 tell the command for doing through terminal?

---

### Post by pastalavista on 2008-12-03
I upgraded with the command: ```
sudo aptitude dist-upgrade
``` but have been informed that it doesn't work any more. I believe now it is ```
sudo aptitude safe-upgrade
``` or some such. My upgrade went without a hitch, except a slight problem with wireless after suspend. It has already been fixed.

edit: the new aptitude command is "safe-upgrade" but the replacement for "dist-upgrade" is "full-upgrade" which is more likely to create dependency issues with installed packages but basically the same as "dist-upgrade"

---

