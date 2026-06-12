---
title: "aptitude"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by slakkie on 2009-02-05
Hello all,

Can someone help me for a quest for information regarding aptitude.

From the manpage:

> 
       safe-upgrade
           Upgrades installed packages to their most recent version. Installed packages will not be removed unless they are unused (see the section “Managing Automatically
           Installed Packages” in the aptitude reference manual); packages which are not currently installed will not be installed.

           It is sometimes necessary to remove or install one package in order to upgrade another; this command is not able to upgrade packages in such situations. Use the
           full-upgrade command to upgrade as many packages as possible.

       full-upgrade
           Upgrades installed packages to their most recent version, removing or installing packages as necessary. This command is less conservative than safe-upgrade and
           thus more likely to perform unwanted actions. However, it is capable of upgrading packages that safe-upgrade cannot upgrade.

           Note
           This command was originally named dist-upgrade for historical reasons, and aptitude still recognizes dist-upgrade as a synonym for full-upgrade.



safe-upgrade and upgrade are as far as I can see similar commands, and so are full-upgrade and dist-upgrade. Why did they change the names of these actions?

---

