---
title: "Monitor changes to system after program launch"
date: 2008-11-18
forum: General Help
---

### Post by wongjos1 on 2008-11-18
Here's the problem I'm trying to solve. I am using program which fails to launch on it's first try. If I stop the program and relaunch it, there are no problems. The program is the multiple desktop manager, aka mdm from c3sl.
Here's what happens. I turn on the computer, login, and run "sudo /etc/init.d/mdm start". The program trys to run but fails. After a few seconds I run "sudo /etc/init.d/mdm stop", wait a few seconds for it to kill the program then rerun "sudo /etc/init.d/mdm start" and the program starts with no problems. I've already tried dumping "ps -e" to a file before and after the start and stop commands. Dumping env to a file also reveals that there are no differences. Does anyone have any suggestions on what might be changing to allow the program to run properly on the second time around?

---

