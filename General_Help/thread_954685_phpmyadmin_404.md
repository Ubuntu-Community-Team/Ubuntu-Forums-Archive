---
title: "phpmyadmin 404"
date: 2008-10-21
forum: General Help
---

### Post by markme on 2008-10-21
hi

im new to linux, but ive been going around in circles with this since friday, i must have read through every phpmyadmin installation problem under the sun, but still no fix.

i have rented a dedicated server from fasthosts.co.uk, which is running ubuntu dapper, php5, mysql5 and apache2. phpmyadmin appears to install ok, but when i visit http://<myip>/phpmyadmin
all i see is a 404. http://<myip> will load up pages as expected.

phpmyadmin appears to be installed in /etc/phpmyadmin, though i have also had it in /usr/share/phpmyadmin, and i have been using a symlink to send web users to these folders like so 

ln -s /etc/phpmyadmin /var/www/phpmyadmin

on searching at command prompt for a file which i know exists in htdocs, i see the path 

/home/default/mywebsite.com/user/htdocs/intro.css

so...

i tried to create a symlink -

ln -s /etc/phpmyadmin /home/default/mywebsite.com/user/htdocs/phpmyadmin

this brings up phpmyadmin, but not as i would expect (it shows me it as directory listings). However, on no sites have i seen this method used so am sure it's pretty incorrect.

something which may or may not be related, is that when logging in a message appears - could not chdir to home directory /root: no such file or directory

any pointers on this would be much appreciated as i am losing the will to live.

thanks

mark m

---

### Post by markme on 2008-10-21
is there a reason why i can't just ftp the phpmyadmin folder into my htdocs and password protect it with htaccess?

---

### Post by Ryadt on 2008-10-21
It could be that it's an issue with Dapper as it is not supported anymore by the ubuntu team.

---

### Post by markme on 2008-10-21
you might be right ryadt, but i feel there must be a way to make this work. ive tried creating a file called test.html from the command prompt and placing it into /var/www/ directory. from what i can gather i should now be able to go to www.<mydomain.com>/test.html - all i get is a 404. any files which i upload to my server via ftp work ok from a web browser though. does anyone know of a fix for this, a guide as to what i might be able to do?

thanks mark m

---

### Post by markme on 2008-10-22
this has now been resolved. for anyone with the same issue - The _domain_skel_ folder contains the files that are copied to each domain when the domain is added through the Matrix Control Panel. For example, if you placed the install files for PHPmyAdmin in the _domain_skel_ folder, each domain you add in future would contain all the PHPmyAdmin files.

The path to a specific domain is as follows:

/home/<groupname>/<domainname>/user/htdocs/

where <groupname> is the name of the group containing the domain, and <domainname> is the domain in question.

---

