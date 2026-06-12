---
title: "in what log should I look for..."
date: 2008-11-11
forum: General Help
---

### Post by Mia_tech on 2008-11-11
the avscan which is the clamav front end interface suddenly fired up today, and I got my AV to run on sundays, and it is scheduled to run in the background as "clamscan" using crontab.... I just checked my crontab file and neither clamav or avscan are scheduled to run today, so I decided to take a look at the logs file I did a search using System>Administration>System logs for "avscan" but nothing showed up related... anyway, in what log specific could I find a command or application that was ran on my pc?...I usually find it in auth.log, but this time I've looked everywhere and nothing...and something should've fired that application.... could anyone give me some clues here?

thanks

---

### Post by Bobby Rankin on 2008-11-11
I don't believe that Ubuntu, by default, logs every command that is run. That would be a huge file.

---

### Post by ciscosurfer on 2008-11-11
Take a look under /var/log

This might also be helpful: [http://www.clamav.net/doc/latest/](http://www.clamav.net/doc/latest/)

---

### Post by Sam on 2008-11-11
> **Bobby Rankin said:**
> I don't believe that Ubuntu, by default, logs every command that is run. That would be a huge file.

Thats why there is an automatic log rotation which split the log files and compress them when they reach a specific size. Have a look in /var/log.


EDIT: Silly typo.

---

### Post by Mia_tech on 2008-11-11
> **Sam said:**
> Thats why there is an automatic log rotation which split the log files and compress them when they reach a specific size. Have a look in /var/www.

isn't in /var/www whre your website is hosted..... I wouldn't expect to find anything related to logs there

---

### Post by Mia_tech on 2008-11-11
> **Bobby Rankin said:**
> I don't believe that Ubuntu, by default, logs every command that is run. That would be a huge file.

well I don't expect to see every command the system executes but I would like to see the one executed by users and most definitely by me, which are not been logged... how could turn that on?

---

### Post by Sam on 2008-11-11
> **Mia_tech said:**
> isn't in /var/www whre your website is hosted..... I wouldn't expect to find anything related to logs there

Oops that was wrong ! I type this directory too often I haven't paid attention. It was /var/log.

:oops:

---

