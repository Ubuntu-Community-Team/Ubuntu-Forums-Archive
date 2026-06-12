---
title: "Equivalent of Synaptic &quot;Origin&quot; feature in apt/dpkg?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Ubuntooid on 2009-07-11
In Synaptic there is an "Origin" button among others in left bottom corner which allows to view packages grouped by sources from which they were installed.

Is there a possibility of doing something similar using apt-cache, apt-get or dkpg ?

---

### Post by renbla on 2009-07-11
It seems like there isn't. But why do you need to know it??

---

### Post by Ubuntooid on 2009-07-11
Why? Synaptic takes a while to start on my not-so-new machine, command line tools are far more quicker. Also, I may need to write some bash script that uses this feature in the future.

---

### Post by oldos2er on 2009-07-11
I think 'origin' can be found with dpkg-query. Not sure of the syntax though, but you can look here: [http://manpages.ubuntu.com/manpages/karmic/man1/dpkg-query.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/dpkg-query.1.html) .

---

### Post by Ubuntooid on 2009-07-13
Command
```
dpkg-query -W -f '${Package}\t${Origin}'
```
shows the same as
```
dpkg-query -W -f '${Package}'
```,
that is it doesn't show anything for Origin. 

I've found some Python script at [http://goonmill.org/static/dpkg-origins]("http://goonmill.org/static/dpkg-origins") that does what I wanted.

Also at [http://lists.debian.org/debian-user-french/2005/08/msg01157.html]("http://lists.debian.org/debian-user-french/2005/08/msg01157.html") someone has written interesting scripts, but comments are in French.

---

