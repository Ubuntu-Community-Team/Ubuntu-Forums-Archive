---
title: "ubuntu hardy quiting to text mode unexpectedly"
date: 2008-08-23
forum: General Help
---

### Post by lwyic on 2008-08-23
I'm running ubuntu hardy on my T60 with Gnome desktop. Sometimes, when I click on a windows' title bar, it will drop to text mode unexpectedly. Then I don't know what to do to restore it... I would then need to crtl-alt-1 to login and then restart it. it's been very annoying.

---

### Post by cmnorton on 2008-08-23
Start by looking in your logs (/var/log) and viewing the output of dmesg right after this happens. The fact you go to text mode should make this easier to do this. I would also post this as a bug in Ubuntu launchpad. Provide log info, and your installation information. Under /var/log, this log file beings -- I think -- with dpkg.

---

