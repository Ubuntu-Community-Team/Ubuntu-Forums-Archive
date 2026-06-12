---
title: "Upgrading Ubuntu from 8.04 to 8.10 update-manager breakage"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by SableSlayer on 2008-12-24
I'm trying to upgrade from Ubuntu 8.04 to 8.10 and i've just had a update-manager breakage :( 

What happened was i did "sudo update-manager -c -d" without enabling the repos.

here is the error that it gave me

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

any help would be greatly appreciated

---

### Post by SableSlayer on 2008-12-24
i fixed the problem by typing "sudo apt-get upgrade" and then restarting the computer. Thanks for anybody who tried to help.

---

### Post by zoundz on 2008-12-24
If you go to your system tray, I would assume you have updates to install. At the top of that update window there should be an update button.

---

