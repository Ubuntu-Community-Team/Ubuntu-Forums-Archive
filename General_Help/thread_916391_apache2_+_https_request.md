---
title: "apache2 + https request"
date: 2008-09-10
forum: General Help
---

### Post by mickey13 on 2008-09-10
Hi all,

Is there a way to see if apache2 is getting a https request?  I have apache2 listening on port 443, and on my local network it seems to work.  When I try to do the request using my static IP, it doesn't work.  I've ensured that my router is forwarding the correct port (and the software firewall is open as well on port 443).  So I'm now trying to make sure that the https request is actually getting to apache2.  Thanks in advance for the help.

Mickey

---

### Post by iaculallad on 2008-09-10
Try looking at Apache2 log file directory:

> /var/log/apache2

---

### Post by mickey13 on 2008-09-11
Ok, in the access.log, I'm getting an entry when I connect through http, but not https.  So the request isn't getting to apache2.  I've ensured that my router is forwarding the port and that the software firewall is allowing the port in.  Is there anything else I can check to see where the breakdown is?

---

