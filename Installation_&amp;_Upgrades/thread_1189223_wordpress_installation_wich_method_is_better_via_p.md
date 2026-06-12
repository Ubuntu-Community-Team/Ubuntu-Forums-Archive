---
title: "wordpress installation: wich method is better: via package management or manually?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by jdarias on 2009-06-16
I have a wordpress installation in my didactic server. I´m interested in learning all related to this blogging platform. 
But when i tried to install some plugins or update wordpress itself, i ran into problems: it said it couldn´t find or create /usr/share/wordpress
So in order to avoid this kind of problems, what is the best method to install it? manually, downloading it from wordpress.org or using the provided (and non updateable, customizable) package?

EDIT: I´m on wheels now! I did aptitude purge wordpress and installed the just released 2.8 release. i chmoded the folder so my ftp username could write it, and now it works beautifully!
It removed some dependencies, wich, for what it seems are not needed to make it work... for now (nor they are mentioned in the wordpress documentation)... will check and see...

---

