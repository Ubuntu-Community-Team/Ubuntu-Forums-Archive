---
title: "Eclipse and Tomcat integration"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by rambuntu1 on 2008-12-31
Hey,

I have installed the latest Tomcat version using synaptic package manager.
It installed the base in /var/lib/tomcat...
and home in /usr/share/tomcat6... which is by default.

I tried choosing the installation directory as
/usr/share/tomcat6... and it was complaining of 'conf' folder missing.
which is present in /var/lib/tomcat.. 
when i tried the base directory, it was throwing me of as bin is missing...

Could someone throw some ideas... of how do i configure this....

---

### Post by tigretigre on 2009-06-17
I went to /var/lib/tomcat6 and symlinked to the bin and lib directories of /usr/share/tomcat6 and it seemed to do the trick.

Titi

---

