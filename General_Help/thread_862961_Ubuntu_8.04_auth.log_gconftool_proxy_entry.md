---
title: "Ubuntu 8.04 auth.log gconftool proxy entry?"
date: 2008-07-18
forum: General Help
---

### Post by wargames on 2008-07-18
Hi, I just installed Ubuntu 8.04 lately and noticed a entry that keeps appearing in my auth.log file. Can someone explain what it means and what it is for?

Jul 17 22:14:27 me-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session opened for user me by (uid=0)
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session closed for user me
Jul 17 22:14:27 me-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session opened for user me by (uid=0)
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session closed for user me
Jul 17 22:14:27 me-laptop sudo:     root : TTY=unknown ; PWD=/ ; USER=me ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session opened for user me by (uid=0)
Jul 17 22:14:27 me-laptop sudo: pam_unix(sudo:session): session closed for user me

---

### Post by wargames on 2008-07-19
bump

no one knows?

---

### Post by asmoore82 on 2008-07-27
I can confirm the same messages in my auth.log;
it seems to be happening at the same time daily.

---

### Post by asmoore82 on 2008-07-27
they are caused by the `apt` cron script that runs daily;
it is located at "/etc/cron.daily/apt" ...

---

### Post by wargames on 2008-08-04
Ok, so I guess this is a normal part of apt. Thank you. :)

---

### Post by Jhongy on 2009-01-22
Just noticed the same thing -- glad I found the answer :-)

---

