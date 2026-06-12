---
title: "can't install any package"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by thesilverline on 2009-02-05
Before I thought this problem was only with firebird. But now I found it is associated with all the installlations. I tried installing tomcat and then jetty , but all the time I got this error:
[I]E: firebird2.1-server-common: subprocess post-installation script returned error exit status 1
E: firebird2.1-super: dependency problems - leaving unconfigured
[/I]Seems like I can't install any application any more. 
Please, teach me how to removed this dependency problem.

---

### Post by oldos2er on 2009-02-05
Check System, Administration, Software Sources to see if you have all repositories enabled.

---

### Post by thesilverline on 2009-02-05
well it's fine now. I ran 
dpkd-reconfigure --all 
which resolved all the dependencies messes and then I re-installed. 
Thanks to all though.

---

