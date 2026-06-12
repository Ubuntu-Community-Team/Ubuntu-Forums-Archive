---
title: "Ubuntu 12.04 - Cds always read as blank?"
date: 2013-06-06
forum: Hardware
---

### Post by todxdurchxfeuer on 2013-06-06
Fresh format and install of ubuntu 12.04 lts. I burn a cd using brasero. Cd-r reads fine on seperate pc running windows. Reinsert cd into ubuntu laptop and it always reads as blank. I get the pop up "you have inserted a blank cd, what action do you wish to take?" any ideas? open the home folder, and view cd and it shows as blank. enter df into terminal with cd in drive and this is what it spits out to me:




joel@joel-Inspiron-1545:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      237308608 11553136 213700844   6% /
udev             1523936        4   1523932   1% /dev
tmpfs             612752      872    611880   1% /run
none                5120        0      5120   0% /run/lock
none             1531872     1812   1530060   1% /run/shm
joel@joel-Inspiron-1545:~$ 



same output without cd in drive. I'm smashing my head against the wall at the moment.

---

### Post by slickymaster on 2013-06-06
[Cannot view, use, or open CDs or DVDs in Ubuntu 12.04]("http://askubuntu.com/questions/144860/cannot-view-use-or-open-cds-or-dvds-in-ubuntu-12-04")

---

### Post by todxdurchxfeuer on 2013-06-06
This solved my problem. Thank you very much.

---

### Post by slickymaster on 2013-06-06
You're welcome. Glad you got it working.

Please, don't forget to mark the thread as SOLVED. See the link in my signature if you don't know how to do it.

---

