---
title: "Lemon POS Installation"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by kmuzheri on 2009-11-06
Hello Guys.
I managed to install the Lemon POS software but now I can not connect it to the database. I installed mysql server. There is a script file called **lemon_mysql.sql** that is usedto create the database structure but I can not find it in my installation. I have checked the folders**  /usr/share/apps/lemon/ and /usr/local/share/apps/lemon/** but there is nothing. I installed Lemon POS 0.7, where can I get the script file [B]lemon_mysql.sql.

[/B]Thanks in Advance

---

### Post by mchavezg on 2009-11-07
There is newer version of lemonpos.
Try to get the new one (0.8)

There is one .deb package of lemonpos 0.8 for (k)ubuntu karmic koala (9.10). Also, there is newer code at the SVN under persa branch with good improvements... Now lemonpos can use any CUPS printer to print tickets (just tell cups to fit the page) on termal printers. I have tested the Star TSP100 (143) printer. Of course to take this new features you will need to compile lemonpos from sources.

There is a wiki at:

[http://apps.sourceforge.net/mediawiki/lemonpos/](http://apps.sourceforge.net/mediawiki/lemonpos/)

The compile/install guide is :
[http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide)
[http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=A_kubuntu_specific_installation_guide](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=A_kubuntu_specific_installation_guide)

---

