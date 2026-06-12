---
title: "Updating Issue, possibly Java related"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by RedStickHam on 2009-04-26
I upgraded from 8.10 to 9.04 and even though it took a few hours(slow downloads, probably due to overworked servers) it's running fine.  This morning I ran the update manager just to see if there were any updates available yet and got this message:

NOT ALL UPDATES CAN BE INSTALLED.
Run a partial update to install as many updates as possible.
This can be caused by
A previous update that did not complete
Problems with some of the installed software
Unofficial Software packages not provided by Ubuntu
Normal Changes of a pre-release version of Ubuntu

When I try to run the partial upgrade, it says these are the changes it will make:

Remove libd4.5-java
install libass1
install libd4.6-java
install libd4.6-java
install libd4.6-java-gcj
install libdca0
install liblrdf0
install libmodplug0c2
upgrade liblucene2-java

When I click to start the upgdate, the update manager just closes down.

The only unofficial piece of software I had on 8.10 that didn't come from an Ubuntu repository was OpenOffice 3.0, which I installed from their repository.

Any ideas?

RedStickHam

---

### Post by Triptol on 2009-04-26
I kinda like solving these problems with the following command:
```
aptitude dist-upgrade
```
Now, this command might remove more programs than you want. The trick is to note what it is going to deinstall and then when it is done, install the lost programs.

---

