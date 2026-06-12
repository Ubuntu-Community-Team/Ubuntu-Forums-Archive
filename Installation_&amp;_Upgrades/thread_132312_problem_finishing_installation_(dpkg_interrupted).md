---
title: "problem finishing installation (dpkg interrupted)"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by v3rtigo on 2006-02-18
hey i wanted to try ubuntu but i have many problems with the install
after it enjected my cd and rebooted ubuntu loaded fine w/o any problem
and started automaticly instaling programs, after a while in mid gnome install
it crashed and didn't even let me set root password or anything in ubuntu
i needed to chroot from gentoo livecd to set root password
and connect to the internet because i see cable dialer.

the only thing it showed was

"dpkg was interrupted, you must manualy run dpkg --configure -a to correct the problem"

but if i try i just have new set of errors about dpkg,
if i try to run apt-get
it just tells me


"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first"

---

### Post by anirban.sam on 2006-02-18
kill any daemon running in background like synoptic or apt-get, this will solve the lock issue

you dont need a root, use sudo to start a command with root previlage, use yr user passwd

sudo apt-get update will solve dpkg problem

---

