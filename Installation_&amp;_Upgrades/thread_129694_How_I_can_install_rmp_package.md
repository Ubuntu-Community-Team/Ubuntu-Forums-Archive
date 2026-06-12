---
title: "How I can install rmp package?"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by wint on 2006-02-14
In Ubuntu there is no command :
#rpm

So I can't install rpm package like in redHat(Fedora Core)... But I think must be another way to do it....

---

### Post by ajgreeny on 2006-02-14
I think it is "dpkg -alien filename" or something like that.  I've never used it so can't help further but a search of the forum should help more.

---

### Post by jamesford on 2006-02-14
its sudo alien whatever.rpm
this produces whatever.deb
you then install using sudo dpkg -i whatever.deb

you should probably download a deb package instead of rpm if its available though

---

### Post by frodon on 2006-02-14
A nice guide : [http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)

---

