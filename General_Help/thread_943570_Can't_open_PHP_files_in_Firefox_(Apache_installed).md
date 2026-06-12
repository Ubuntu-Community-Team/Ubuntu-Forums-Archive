---
title: "Can't open PHP files in Firefox (Apache installed)"
date: 2008-10-10
forum: General Help
---

### Post by tonyr1988 on 2008-10-10
I've got the entire LAMP configuration installed, and this used to work. Apparently it doesn't anymore.

I threw my project in /var/www/folder-name, and the permissions should be set correctly (I made everything in there, including the folder, 777 to check).

I navigate to localhost, and I see "Index of /" with "Apache/2.2.8 (Ubuntu) Server at localhost Port 80" along the bottom. I see the folder. When I click on the folder, Firefox pops up with:

> You have chosen to open:

which is a PHTML file.
What would you like to do?

(yeah, the name is blank)

If I navigate directly to localhost/folder-name/index.php, it gives me a similar message:

> You have chosen to open:
index.php
which is a PHP file.

I restarted Apache (sudo /etc/init.d/apache2 restart) and it seems to be working fine (otherwise it wouldn't even give me the index page, right?).

What else should I check to see if everything is working properly?

---

### Post by Paul41 on 2008-10-10
Did you try clearing your browser cache after restarting apache? I doubt it will make a difference but worth a try. I have seen someone say this fixed there problem with this before.

---

### Post by sillyxone on 2008-10-10
look like your Apache doesn't know how to handle .php file. You can try to reinstall libapache2-mod-php5 package again, see if it can reset the configuration of Apache.

The permission seems to be OK.

---

### Post by Sycron on 2008-10-10
I had once this problem too and after I restarted apache everything works like a charm.

---

### Post by scottdky on 2009-05-28
Clearing the cache worked for me. I had messed with my php.ini file in lampp, and then had this problem with opening a phtml file. Neither restarting lampp nor rebooting helped. Clearing Firefox's cache did the trick.

---

### Post by Parapan on 2010-10-06
Wow, this is weird, but its true. Restarting the cache in firefox did the trick for me. Glad i found this post or im sure i would have stayed up trying to fix this one. :P

---

