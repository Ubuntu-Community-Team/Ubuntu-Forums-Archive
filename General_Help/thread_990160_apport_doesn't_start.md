---
title: "apport doesn't start"
date: 2008-11-22
forum: General Help
---

### Post by biasquez on 2008-11-22
apport doesn't start like service. i enabled it:

cat /etc/default/apport
# set this to 0 to disable apport, or to 1 to enable it
enabled=1


sudo /etc/init.d/apport start
Starting automatic crash report generation:: apport.
/etc/init.d/apport: 103: runlevel: not found

I haven't modified the init script. I already reinstalled apport.

---

### Post by biasquez on 2008-11-25
FIXED: reinstall lsb-base

---

