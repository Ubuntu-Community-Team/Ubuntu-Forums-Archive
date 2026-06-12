---
title: "[SOLVED] How to delete files belonging to www-data with a user account?"
date: 2008-09-11
forum: General Help
---

### Post by mermshaus on 2008-09-11
Hello,

I've got a cache directory in which I write files using a PHP script running under Apache. The directory belongs to my normal user account (user: marc, group: marc), the created cache files are owned by the Apache (?) user (0644 (don't want to change that), u: www-data, g: www-data).

Is there a way to delete the files without resorting to sudo? I am trying to write a little clean-up script (using Apache Ant) and I don't want to type my password all the time or something like that.

Would it be a good idea to run Apache under my normal user account instead of www-data? I can't think of anything else. It's quite annoying.

Thanks,

-- Marc

---

### Post by hwttdz on 2008-09-11
Can't you make the cleanup script owned by the apache user?  That way the user will be deleting their own files.

---

### Post by bodhi.zazen on 2008-09-11
change ownership of the temp directory to root.www-data with permissions of 660 .

---

### Post by mermshaus on 2008-09-20
I apologize for answering so late, I had an assignment to finish. Thanks for your ideas. For the timing being I took the easy way out and changed user and group of the Apache service in /etc/apache2/apache2.conf and /etc/apache2/envvars respectively (see [documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP#Edit%20Apache%20Configuration")).

That's probably not the best or most secure thing to do but it's got the advantage that all similar cases inside the wwwroot folder are also solved.

---

### Post by pe7er on 2008-10-13
> **mermshaus said:**
> For the timing being I took the easy way out and changed user and group of the Apache service in /etc/apache2/apache2.conf and /etc/apache2/envvars respectively
Thanks!
I was looking for something similar, but could not find www-data in /etc/apache2/apache2.conf or /etc/apache2/http.conf

Thanks to your post I was able to locate it in /etc/apache2/envvars 
So I changed it with:
```
sudo gedit /etc/apache2/envvars
```
From:
> export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

to:
> #export APACHE_RUN_USER=www-data
export APACHE_RUN_USER=some_user
#export APACHE_RUN_GROUP=www-data
export APACHE_RUN_GROUP=some_user


---

