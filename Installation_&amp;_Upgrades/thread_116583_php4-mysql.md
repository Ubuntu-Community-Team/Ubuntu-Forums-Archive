---
title: "php4-mysql"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by Tux_Phoenix on 2006-01-13
When I do a apt-get install php4-mysql I get a error.  I took a Screen shot...

[[IMG]http://img209.imageshack.us/img209/1452/aptgetprobthumb2tu.jpg[/IMG]]("http://img206.imageshack.us/img206/2100/aptgetprob5ud.jpg")

Any Ideas?  I am setting up a web server and got hung up on this majorly.  I did a server install so I have no gui.

---

### Post by nkhansen on 2006-01-13
According to packages.ubuntu.com, php4-mysql is in the universe repository. You can add the repository by uncommenting the appropriate lines in /etc/apt/sources.list

Procedure:
$ sudo nano /etc/apt/sources.list
(uncomment lines)

$ sudo aptitude update (or apt-get, if you insist)

$ sudo aptitude install php4-mysql (apt-get is still possible)

Good luck with the web server!

---

### Post by Tux_Phoenix on 2006-01-13
THANK YOU SO MUCH.  I have been working on this for 2 days.

---

