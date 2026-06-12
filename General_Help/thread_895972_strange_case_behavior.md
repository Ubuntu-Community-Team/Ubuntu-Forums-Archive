---
title: "strange case behavior"
date: 2008-08-20
forum: General Help
---

### Post by washakie on 2008-08-20
Hello, 

I'm trying to mount an external USB drive to use for backup with either rsync or unison. I am trying to use the USB drive as a primary backup for two computers, one Kubuntu, one windows XP.

The mounting seems to work, but for some reason my directories that are all caps, for example ~/SCO shows up on the linux side as ~/sco, but I can still cd to /SCO ... see below:

$ cd sco
$ ls
COMS-Reporting  Data_server  Presentations  ProjectPlans  webserver
$ pwd
/media/TUTTO/07/sco
$ cd ../SCO
$ ls
COMS-Reporting  Data_server  Presentations  ProjectPlans  webserver
$ pwd
/media/TUTTO/07/SCO

is there an explanation for this?

THanks!

---

### Post by unutbu on 2008-08-20
Some filesystems such as ext3 are case-sensitive, but others, like FAT are not. Perhaps /media/TUTTO has been formatted with a case-insensitve filesystem type.

See Dan Espen's post [http://www.usenet-forums.com/linux-general/85996-linux-unix-case-sensitive-case-insensitive.html](http://www.usenet-forums.com/linux-general/85996-linux-unix-case-sensitive-case-insensitive.html)

---

