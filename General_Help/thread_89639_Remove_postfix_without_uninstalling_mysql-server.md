---
title: "Remove postfix without uninstalling mysql-server"
date: 2005-11-13
forum: General Help
---

### Post by sanjuro on 2005-11-13
Hi,

I use Ubuntu primarily as a learning+development platform for Python/PHP projects (earlier I was using Windows :) ). Recently I removed/purged unnecessary services/apps which I did not need. One service which I saw running was postfix. I cannot remove this one since mysql-server also has to be removed which I don't want to do. I never needed a mail server as a prerequisite to run mysql on Windows.

Any ideas how I can remove postfix using aptitude/apt-get without removing mysql-server in the bargain ?

Thanks in advance.

---

### Post by Remmelas on 2005-11-13
Wow, i'd think this is a bug.  mysql-server shouldn't depend on postfix.  At any rate, back up your mysql databases to be safe.  Then, let it remove mysql-server when you uninstall postfix, so long as you don't remove with --purge, it should leave your mysql server settings and databases in place so that when you do ```
sudo apt-get install mysql-server
``` is should just pick up the databases right from where you left off.

---

### Post by heimo on 2005-11-13
mysql-server depends on mailx, which requires MTA, but if you don't want postfix, you can always use alternative MTA (for example nullmailer):
[http://packages.ubuntu.com/breezy/virtual/mail-transport-agent]("http://packages.ubuntu.com/breezy/virtual/mail-transport-agent")

And here's the answer to the next question: :)
[http://lists.debian.org/debian-user/2004/11/msg01561.html](http://lists.debian.org/debian-user/2004/11/msg01561.html)

---

### Post by sanjuro on 2005-11-13
[QUOTE=heimo]mysql-server depends on mailx, which requires MTA, but if you don't want postfix, you can always use alternative MTA (for example nullmailer):
[http://packages.ubuntu.com/breezy/virtual/mail-transport-agent]("http://packages.ubuntu.com/breezy/virtual/mail-transport-agent")

And here's the answer to the next question: :)
[http://lists.debian.org/debian-user/2004/11/msg01561.html](http://lists.debian.org/debian-user/2004/11/msg01561.html)[/QUOTE]

Thanx a lot ! Actually that WAS going to be my next question. Though I don't actually need even nullmailer, I have replaced postfix with this for now.

---

