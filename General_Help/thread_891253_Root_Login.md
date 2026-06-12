---
title: "Root Login"
date: 2008-08-15
forum: General Help
---

### Post by mschraier on 2008-08-15
I ma running Kubuntu 8.04.1/KDE 4.1.  I want to login as root so I can make changes in the Systems Setting with regards to auto login.  There is no Administor Mode button.  What can I do?    :guitar:

---

### Post by PCessna on 2008-08-15
> **mschraier said:**
> I ma running Kubuntu 8.04.1/KDE 4.1.  I want to login as root so I can make changes in the Systems Setting with regards to auto login.  There is no Administor Mode button.  What can I do?    :guitar:

I will leave this to be answered, but for security reasons, auto-login is HIGHLY unrecommended.

---

### Post by overdrank on 2008-08-15
> **mschraier said:**
> I ma running Kubuntu 8.04.1/KDE 4.1.  I want to login as root so I can make changes in the Systems Setting with regards to auto login.  There is no Administor Mode button.  What can I do?    :guitar:

Hi and you may read here
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by aysiu on 2008-08-15
Alt-F2 ```
kdesu systemsettings
``` or ```
kdesu kcontrol
``` No need to enable a root login to make root changes.

---

### Post by dualpretop on 2008-08-31
Terminal:

kdesu /usr/lib/kde4/bin/systemsettings

---

