---
title: "Unable to run any administrative applications"
date: 2008-10-30
forum: General Help
---

### Post by FlintZA on 2008-10-30
I have a pretty standard Hardy install. From yesterday for the first time for no apparent reason, I can't run any administrative applications. When I do run them, the "Starting administrative application" (or something like that ;)) app appears in the task bar, as does the application I'm trying to run, but after a few seconds both disappear. I've had no problems running and using admin apps in the past. Can anyone suggest what might be the problem, or where I could look to get a clearer idea of what's going on?
I don't have an internet connection on the machine, so I cant apt-get any diagnostic tools you might suggest that aren't in the default install.

---

### Post by zvacet on 2008-10-30
```
gksudo gedit /etc/hosts
```

and look if first two lines look like 

127.0.0.1 localhost
127.0.1.1 host

**host = your comp name**

---

### Post by FlintZA on 2008-12-03
Thanks, that led me straight to the problem. I have two network configurations, and my home one had my work domain specified.

---

