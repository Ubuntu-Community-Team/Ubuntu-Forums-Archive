---
title: "Viewing dmesg from a previous session"
date: 2008-09-10
forum: General Help
---

### Post by devosion on 2008-09-10
Ubuntu Hardy has been hard freezing on me on occasion since its install, and its forced me to perform a hard reboot everytime since it does not respond to alt+prnt-screen+k,r,s,e,i,u,b. Problematically dmesg only seems to display messages from a current session and when the pc isnt responding this isnt possible. How can I view my error log from a previous session, or have it inputted to a text file upon or before the crash?

---

### Post by iaculallad on 2008-09-10
> **devosion said:**
> Ubuntu Hardy has been hard freezing on me on occasion since its install, and its forced me to perform a hard reboot everytime since it does not respond to alt+prnt-screen+k,r,s,e,i,u,b. Problematically dmesg only seems to display messages from a current session and when the pc isnt responding this isnt possible. How can I view my error log from a previous session, or have it inputted to a text file upon or before the crash?

Past dmesg messages are automatically archived (with the newest file named as dmesg, old files archive name as dmesg.1.gz..etc..). The archive files are stored in this location: /var/log.

---

### Post by devosion on 2008-09-10
Thank you for your assistance!

---

