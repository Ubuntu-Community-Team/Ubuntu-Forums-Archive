---
title: "buffer I/O error on device hdb"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by corytoneill on 2006-01-19
i ran the command > sudo get-apt update
sudo get-apt ubuntu-desktop

and got
> buffer I/O error on device hdb

---

### Post by dcstar on 2006-01-19
[QUOTE=corytoneill]i ran the command 

and got[/QUOTE]
hdb is whatever IDE device you have as the Slave on the first active IDE channel Ubuntu finds, if it is your CD-ROM then you may have a compatibility problem - or it is looking for the Ubuntu install disk.

What does: "hdparm -i /dev/hdb" show?

---

### Post by dbist on 2007-04-19
I believe the right command is:

sudo apt-get update
sudo apt-get ubuntu-desktop

I never tried your way so won't say you're wrong. I am investigating my own Buffer I/O error, and so far all of the forums say it may be the CD-ROM drive.

---

