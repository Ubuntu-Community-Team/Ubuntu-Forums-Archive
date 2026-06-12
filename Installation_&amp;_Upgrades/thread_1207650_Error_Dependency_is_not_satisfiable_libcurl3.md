---
title: "Error: Dependency is not satisfiable: libcurl3"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by mytechguru on 2009-07-08
hi,
     i am new to linux. while surfing i needed swf player so i tried to install adobe flash player linux package. but it is showming some error message "Error: Dependency is not satisfiable: libcurl3"


My Current OS is Ubuntu Stable Version.

---

### Post by az on 2009-07-08
What version of Ubuntu are you running?

Did you first install that version or have you upgraded from previous versions?  Do you have software from a different version of Ubuntu installed on your current installation?

Most importantly, are all the sources in your software channels set to the same version of Ubuntu?

---

### Post by mytechguru on 2009-07-08
My Current version of ubuntu is 9.0.4 Current stable version . i have installed fresh ubuntu .

---

### Post by synapsys on 2009-07-08
If you install 'flashplugin-nonfree' package in synaptic, it should install all the dependencies it needs. It seems you are trying to install a .deb package (downloaded from the internet) which only installs that package, nothing else.

---

