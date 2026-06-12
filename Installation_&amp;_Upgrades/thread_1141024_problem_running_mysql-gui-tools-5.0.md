---
title: "problem running mysql-gui-tools-5.0"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by sirpelidor on 2009-04-28
hi,

Running 8.04 with mysql 5(ubuntu packaged) installed.  was looking for a db client too and i downloaded /mysql-gui-tools-5.0 from mysql's website.


when tried to run the app in the shell, nothing comes up.  all i see in the shell stated:
```

 ./mysql-query-browser
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 17: invalid match target "scan"
Fontconfig warning: line 73: unknown element "cachedir"

```

i visited all my log files at /var/log/mysql but i don't see anything.  anyone experienced something like this?

thank you

---

### Post by gg234 on 2009-04-28
try to install phpmyadmin

sudo apt-get install phpmyadmin

this very simple tool

---

