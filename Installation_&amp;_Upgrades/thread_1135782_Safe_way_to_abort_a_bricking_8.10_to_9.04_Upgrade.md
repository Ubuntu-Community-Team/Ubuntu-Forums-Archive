---
title: "Safe way to abort a bricking 8.10 to 9.04 Upgrade?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by xianthax on 2009-04-24
been on the "Installing the upgrades" part of the 8.10 to 9.04 update process for a few hours now, terminal output of the distribution upgrade window is showing is a constantly running string of:

y
y
y
y
y
y
y
y
y
y
y
y
y

continually running, assuming its trying to answer a question that wasn't asked or something like that.

is there a "safe" way to kill this and figure out what the problem was?

cheers,

xian

---

### Post by xianthax on 2009-04-24
ushare is culprit

killed the upgrade process (must do from terminal, system monitor wouldn't let me)

removed ushare

re-ran upgrade manager, it will ask you to do a partial upgrade, do that..

had to reinstall driver from nvidia, revert to amarok 1.4 (2.0 sucks), and move to a ppa for VLC as embedded mode seems to be broken in the repo packages...

otherwise all seems well...

---

