---
title: "Automatic file execution"
date: 2008-07-22
forum: General Help
---

### Post by skipsbro on 2008-07-22
I run a simple backup monthly of some key files by putting them into a Gzip tar archive and then burning them to a CD and I was wondering if there's any way I could get my back-up shell script run monthly automatically.

---

### Post by Potatoj316 on 2008-07-22
Yes you can!

You have to creat a cron job, they execute scripts at regular intervals.  Heres the link...

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

### Post by Potatoj316 on 2008-07-22
For the crontab you could do something like

crontab -e (to edit the crontab)
00 12 01 * * /bin/path/to/file

this makes it run at noon every 1st day of the month

---

### Post by spiderbatdad on 2008-07-22
/etc/cron.monthly  make the script owned by root, I believe. I have never personally run cron jobs, but it is my understanding this is the purpose of the directory.

---

