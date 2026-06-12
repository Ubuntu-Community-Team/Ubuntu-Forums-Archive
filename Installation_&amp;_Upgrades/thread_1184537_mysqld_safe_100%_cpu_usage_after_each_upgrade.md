---
title: "mysqld_safe 100% cpu usage after each upgrade"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by chombium on 2009-06-11
Hi,

After the last few updates of my Ubuntu box (jaunty - 9.04) I've noticed that after/during the execution of the update manager the CPU usage rises up to 100% and it remains that way after the update is finished.
Running "top" I've noticed that there is a mysqld_safe (mysql) process running as root. I assume this is started during the upgrade.
After killing this process "sudo kill -9 PID" everything gets back ti normal.

My machine is: Dell Inspiron 1526 AMD64 Turion.

Is this a bug?
How can I fix this?

BR, Jovan

---

