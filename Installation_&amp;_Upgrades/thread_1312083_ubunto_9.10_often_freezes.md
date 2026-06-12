---
title: "ubunto 9.10 often freezes"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by dreampen on 2009-11-02
Without apparent reasons, ubunto9.10 freezes my desktop. When it happesn, my mouse can still move around. But ubunton 9.10 deosn't respond to any mouse click. 
My keyboard is dead too. Any clue what's going on?

---

### Post by lswb on 2009-11-02
Check your log files for possible clues. Ones to look at are /var/log/syslog and /var/log/Xorg.0.log.old

You can view them in a terminal with the command "less /var/log/syslog"

---

