---
title: "How to enable php5 module for ONLY 1 virtual website."
date: 2008-10-31
forum: General Help
---

### Post by xersist on 2008-10-31
I have installed a new ubuntu lamp server and am switching from apache1/php4 to apache2/php5. I used to be able to enable php for only specific virtual websites hosted. I am unable to see why or where I have it configured wrong to do this on the new server.

Even if remove the sym link in /etc/apache2/modules-enabled/php5.conf I am still able to serve php pages for any virtual website.

I am running U8.04 server and phpmyadmin is also installed.

I can't see where the problem is even after comparing the different configs.

Simply put, by default I need php to be disabled globally and only work if I put the "AddType application/x-httpd-php .php" directive in the VirtualHost section.

Any help please?

UPDATE: I just installed 8.10 and the same issue applies. Fresh install w/ LAMP, if you delete the php5.conf file php still works with just the module installed. 
I don't see anywhere where php AddType is defined when I remove that conf file.

---

