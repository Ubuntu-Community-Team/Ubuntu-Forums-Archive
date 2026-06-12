---
title: "matrix control panel and locating webroot"
date: 2008-10-21
forum: General Help
---

### Post by markme on 2008-10-21
hi

has anyone had any experience with fastosts, or more importantly matrix control panels?

i am having trouble locating the root directory of my website via ssh command line as the matrix cp seems to have confused things.

when i look at the files of my website via ftp, i can see phpinfo.php, which is preinstalled by fasthosts when my server is built. on  searching for phpinfo.php from the command line, it shows that that the only place the file appears is in the directory - /opt/matrixsa/conf/_domain_skel_/user/htdocs/ - i assume that this is my root directory? if so, why is my web root accoring to apache2 set to /var/www/

all of the files in this directory tie in with what is viewable via my ftp program immediately after my server has been built, but if i add or modify any of the files over ftp, the files in /opt/matrixsa/conf/_domain_skel_/user/htdocs/ when viewed from command promt remain unchanged.

the command line and ftp dont appear to correlate at all except immediatly after the server has been built. I have been trying to figure this out since friday, it is driving me crazy.

google searching reveals very little information about matrix cps, i have managed to find a post on a business forum of a similar problem to mine also using a fasthosts dedicated server, but it has never been resolved, the only lead i have from it is that maybe im looking in server root, and i need to be looking in site root?

anyone know of a document source for matrix and how they cooperate with the linux system, as there really is very little online?

thanks

mark m

---

### Post by markme on 2008-10-22
this has now been resolved. for anyone with the same issue - The _domain_skel_ folder contains the files that are copied to each domain when the domain is added through the Matrix Control Panel.  For example, if you placed the install files for PHPmyAdmin in the _domain_skel_ folder, each domain you add in future would contain all the PHPmyAdmin files.

The path to a specific domain is as follows:

/home/<groupname>/<domainname>/user/htdocs/

where <groupname> is the name of the group containing the domain, and <domainname> is the domain in question.

---

