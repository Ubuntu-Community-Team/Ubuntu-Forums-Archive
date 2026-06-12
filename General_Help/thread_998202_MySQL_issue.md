---
title: "MySQL issue"
date: 2008-11-30
forum: General Help
---

### Post by Guy Chapman on 2008-11-30
I've been banging m,y head against a problem moving a mysql database, and have traced the solution; I'd like to append it to this old thread: [http://ubuntuforums.org/showthread.php?t=386056](http://ubuntuforums.org/showthread.php?t=386056) but I can't due to some restriction, so if someone would like to make a note there it would be appreciated.

The steps in Hardy at least are:
&#9675; sudo nano /etc/mysql/my.cnf
&#9675; Change datadir
&#9675; Copy data /dirs
&#9675; Chown mysql:mysql on data /dirs
&#9675; edit /etc/apparmor.d/usr.sbin.mysqld   
&#9675; add  /data/mysql/** rwk,
&#9675; sudo /etc/init.d/apparmor restart

Bingo, MySQL starts in new location.  Apologies if this is already well known, but the above thread is high in Google searches and does not contain the vital apparmor step.

---

