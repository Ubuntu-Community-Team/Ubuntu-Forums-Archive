---
title: "Permissions"
date: 2008-11-19
forum: General Help
---

### Post by FarBeyondHelp on 2008-11-19
:)Hi Guys,

Totally new to Linux so forgive the stupid question.  I'm trying to install the Open Source HelpDesk appliaction called OneOrZero, I've unpacked the folders/files to var/www and I put everything in the ROOT of www.  Now I need to set the file permissions.  In a document I found it says.

cd /home/host/httpdocs/helpdesk/ chown -R www oneorzero/ cd oneorzero/ chmod -R 775 * chmod 777 attachments/ chmod 777 configuration/

Could someone please translate this for me with the path var/www in mind?

Thanks a lot.

Cheers

---

### Post by KeyserSoze93 on 2008-11-19
Which bit is hard to follow?

```
cd /var/www/helpdesk
chown -R www oneorzero
cd oneorzero
chmod -R 775 *
chmod 777 attachments
chmod 777 configuration

```

---

### Post by FarBeyondHelp on 2008-11-20
Well for example "-R www" is www a user?

---

### Post by rampageoberon on 2008-11-20
yes 'www' is a user on your system. You can check the users in the /etc/passwd file

In my experience the user is actually www-data and i'm reluctant to give full read, write, execute (777) permissions to all

---

### Post by FarBeyondHelp on 2008-11-20
Yes that's right, it was www-data - thanks :)

---

