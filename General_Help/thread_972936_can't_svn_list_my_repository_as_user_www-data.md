---
title: "can't svn list my repository as user www-data"
date: 2008-11-06
forum: General Help
---

### Post by nickleus on 2008-11-06
when i change user to www-data:
```
su - www-data
```and then try this:
```
svn list https://example.com/svn/myproject
```i get this error:
> svn: PROPFIND request failed on '/svn/myproject'
svn: PROPFIND of '/svn/myproject': could not connect to server ([https://example.com](https://example.com))i'm doing this because i want to validate the certificate permanently so that my self signed local site gets trusted and saved in www-data's *.subversion/auth* folder in it's home directory: */var/www*
when i run the same svn list command as my normal user everything works fine. why can't i do it as www-data?

---

### Post by nickleus on 2008-11-06
ha ha, it might help if the svnserve and apache2 are running! lol, sorry =)

---

