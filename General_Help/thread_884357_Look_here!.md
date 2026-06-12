---
title: "Look here!"
date: 2008-08-08
forum: General Help
---

### Post by robotman5 on 2008-08-08
ok i install Kubuntu


it installed the KDE Session i did the updates and found out there are 2 broken packages! (no i didnt reload the system)  it might be cause i have Ubuntu and Kubuntu at the same time Hmmmmm:confused:

---

### Post by SuperSonic4 on 2008-08-08
Sounds more like a package/dependancy problem than a (k)ubuntu problem

---

### Post by robotman5 on 2008-08-08
well  i installed the KDE session which i found out how at [www.ubuntugeek.com](www.ubuntugeek.com) :(

---

### Post by SuperSonic4 on 2008-08-08
Are you on Hardy? Because I installed kubuntu over ubuntu by ```
sudo apt-get install kubuntu-desktop
``` in ubuntu

---

### Post by robotman5 on 2008-08-08
yes i am on Hardy

and i am Currenty on the KDE Session

---

### Post by rossjman1 on 2008-08-08
So what's the problem? What packages have errors? Please post some more information.
paste the output of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

---

