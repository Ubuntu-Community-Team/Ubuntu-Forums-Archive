---
title: "Cupsys works for everyone but me, it seems"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by howwhi on 2009-02-20
Thank you in advance for assistance.  Building a new home file/web/db/print server on 8.04 server (no gui on server itself).  Apache is fine, samba is okay (Windows 98 tuning in progress), postgres and mysql are happy.  Cupsys does not like me.

Have modified /etc/cups/cupsd.conf to allow computers on the network access to the cups config screens (:631).  I can connect, I can browse about the admin pages.  LogLevel is debug.

Clue number one, admin user and password are never requested (as I have seen in other implementations).

Connecting from another computer / web browser, page through the "Add Printers" sequence:  name, location; connection via socket://192.168.1.250:9100, select printer (selected HP) and browser hangs.  /var/log/cups/error_log shows a bunch of messages, including "No authentication data provided."  No messages come back to web-browser.

How may I better describe / document these issues for diagnosis??

---

