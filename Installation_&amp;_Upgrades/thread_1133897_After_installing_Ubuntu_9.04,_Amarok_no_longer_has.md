---
title: "After installing Ubuntu 9.04, Amarok no longer has PostgreSQL support"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by denBosch on 2009-04-23
I had Ubuntu 8.10 Intrepid with Amarok set up with a PostgreSQL database, so it was really nice and quick searching my music library.

I've just done a clean install of Ubuntu 9.04, and I want to set up Amarok how I had it before. Unfortunately it **no longer has the option** to use a MySQL or PostgreSQL database (in *Settings > Configure Amarok > Collection*). It also looks very different, but I guess I'll get used to that.

Looking at the Amarok website, it seems that I've now got version 2.0.2 (I guess my old Ubuntu used Amarok 1.x). And it seems that it no longer has PostgreSQL/MySQL support built in.

I've looked at the official How-To at [http://amarok.kde.org/wiki/Postgresql_HowTo](http://amarok.kde.org/wiki/Postgresql_HowTo) which says:
[INDENT]To get PostgreSQL support compiled-in, you need to specify "--enable-postgres" as a configure parameter and re-run "make install" as root. Your configure line probably will look something like this:
```
$ ./configure --enable-postgresql
```
[/INDENT]

But I don't really know about installing from source, and I want to make sure that my Amarok is installed using the proper apt-get thing, so that it gets updated automatically by the system Update Manager.

Any ideas on how I can install Amarok on my Ubuntu 9.04 with PostgreSQL enabled?

---

### Post by PreviousN on 2009-04-27
I'm pretty upset about this issue too. I used to use a mysql server in amarok. I had all my devices (1 laptop, one netbook, and desktop) to use amarok, all using my server to drive the sql server. That would allow me to query my relatively huge database in a matter of 1 or 2 seconds on my netbook. 

Anyways, I'm assuming that the answer is to just reinstall amarok1.4. Should you learn how to do that, please post in this thread! Thx.

---

### Post by AliBi on 2009-05-01
hope this helps:

[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)

greets

---

### Post by munishvit on 2009-05-24
> **AliBi said:**
> hope this helps:

[http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/)

greets

Thanks for this solution...:D

---

### Post by munishvit on 2009-05-24
`

---

