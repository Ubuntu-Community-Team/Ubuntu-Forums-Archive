---
title: "[SOLVED] getting a error message after starting system"
date: 2008-11-29
forum: General Help
---

### Post by avinash389 on 2008-11-29
im gettin ERROR while my sys is doin rotunie check of drivers
it says fsck check of root failed
please can any one help wat happend


after starting system
i'm getting all these .....

checking drive/dev/sda1:8%(stage 1/5,147/1170)
/dev/sda1:Inodes that were a part of a corroupted orphan linked list found.
/dev/sda1:UNEXPECTED INCONSISTANCY ;run fsck MANUALY .
(ie with out -aor -p options)
fsck died with out exit status 4
checking drive/dev/sda1:9%(stage 1/5 , 153/1170)
*an automatic file system check(fsck)of rootfile system failed.
a manual fsck must be performed then the system system restared
the fsck should be performed in readd only mode
*the root file system is currently mounted in read only mode
a maintaince shell is now been started
after performing the maintance press controll -D
to terminate the maintance shell and restart ...

i'm gettin all these after startin my system ...
please help me as i'm new to linux

---

### Post by plucky on 2008-11-29
There is a problem with your file system on your /root partition.To fix it you need to boot your Live Cd and open a terminal **Applications > Accessories > Terminal** and use this command ```
sudo e2fsck -y -v /dev/sda1
```

Do not attempt to run this command on a mounted file system.

To find out what the options are for that command use ```
man e2fsck
``` in a terminal window.

Good Luck

---

### Post by avinash389 on 2008-11-29
thank you plucky for your reply that solves my problem..........

---

