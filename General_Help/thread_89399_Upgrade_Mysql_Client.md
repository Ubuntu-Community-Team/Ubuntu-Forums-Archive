---
title: "Upgrade Mysql Client"
date: 2005-11-12
forum: General Help
---

### Post by atatistcheff on 2005-11-12
I'm trying to access the MySQL version I'm using with LAMPP.  I get the following message from the version of the mysql client installed with Ubuntu:

ERROR 1251: Client does not support authentication protocol requested by server; consider upgrading MySQL client

I've tried the command: apt-get upgrade mysql

This ran for about 40 minutes as it upgraded over 70MB of files none of which appeared to relate to the MySQL client.  I still get the same message.  How can I upgrade this client?

Thanks,
Alex

---

### Post by atatistcheff on 2005-11-12
Ok so I've answered my own question.  I went to the MySQL main site and got the newest client RPM, used alien to convert and install it and it's working fine.  I still have a problem with Snort-mysql though as even the latest version still uses the pre 4.1 mysql client.  Looks like I'll have to work on the authentication issue from the database side rather than the client side...

---

