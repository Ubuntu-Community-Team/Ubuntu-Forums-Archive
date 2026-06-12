---
title: "Apache stopped working after installing proftpd"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by alleycatuk on 2009-08-09
Hi,
I had Apache set up and working fine, available from other PCs on my lan (it's a test server).
I then installed proftpd - install went fine and I can ftp things to and from the test box without a problem.... I then went back to one of my test pages and get this error....

[COLOR=Blue]**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Unknown: Failed opening required '/home/myuser/www/mysite/index.php' (include_path='.:/usr/share/php') in **Unknown** on line **0**
[/COLOR]  
I've had a look on various sites but none mention this happening just after proftpd is installed (that I could find at least). I'm fairly new to Ubuntu - just trying to get a LAMP configuration working well - so any pointers would be great.

Thanks!

---

### Post by alleycatuk on 2009-08-09
Spot the misleading error message! Turns out it was a permissions thing. I didn't have the correct permissions in my site's conf (AllowOverride was none) and I had to set the folder to 777 - that worked ok.

---

