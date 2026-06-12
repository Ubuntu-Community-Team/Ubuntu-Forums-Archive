---
title: "after Upgrading to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ngsupb on 2009-04-24
Hi,

I have upgraded from 8.10 to 9.04.

Trying to fix bugx atm :D

First one that is really annoying is that ctrc+C doesn't work in terminal to interrupt a running command.

so for example I type ping google.com
and can't exit by pressing ctrl+C, it runs the ping command still.

Do you have any ideas?

---

### Post by abo999 on 2009-04-24
Doesn't help (...) but ctrl-C works fine in my terminal after upgrading

---

### Post by gizbun on 2009-04-24
What about Ctrl-z, does that work?

---

### Post by ngsupb on 2009-04-24
yes, Ctrl+Z does work, but Ctrl+Z doesnt stop processes, it just puts it into backgcroung.

But why Ctrl+C doesn't work :((

---

### Post by ngsupb on 2009-04-24
Appears it is a bug

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/350326](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/350326)

ctrl+alt+C works though :)

Probably ctrl+C will be fixed soon.

---

