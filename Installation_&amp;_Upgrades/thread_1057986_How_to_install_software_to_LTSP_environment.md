---
title: "How to install software to LTSP environment"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by djsephiroth on 2009-02-02
Do apps installed on the server then become available on the thin clients, or do packages need to be installed in the thin client chroot?

---

### Post by Pumalite on 2009-02-02
[http://ubuntuforums.org/archive/index.php/t-460111.html](http://ubuntuforums.org/archive/index.php/t-460111.html)
[http://www.disklessworkstations.com/cgi-bin/web/ltspBusiness.html](http://www.disklessworkstations.com/cgi-bin/web/ltspBusiness.html)
[http://www.linuxjournal.com/article/8165](http://www.linuxjournal.com/article/8165)
[http://ltsp.sourceforge.net/ltsp-4.html](http://ltsp.sourceforge.net/ltsp-4.html)

---

### Post by djsephiroth on 2009-02-02
First and second do not appear to apply at all. Third is about soft phones; I shall charitably assume there is something in there about my predicament, but I prefer not to slog through it all for that one tidbit of info. Fourth is just the standard install info for a deprecated version of LTSP, and does not seem to apply.

Figured it out on my own. Answer: stuff installed on the server appears to be accessible on the clients. Rebuilt the thin-client image just to be safe. So far, so good.

---

### Post by haddog on 2009-02-15
You are correct dj. Software installed on the server is accessible on the clients.

---

### Post by djsephiroth on 2009-02-24
Thanks.

---

