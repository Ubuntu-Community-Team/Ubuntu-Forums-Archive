---
title: "FATAL: Cannot connect to MySQL server on 'localhost'."
date: 2008-10-02
forum: General Help
---

### Post by bolds on 2008-10-02
NEWBIE --- 

Hi group, I am having a hard time getting my install of cacti to work. I went through the documentation and did everything it said to do. My issue is when I open a browser to try to get to the front page I get the following error message 

FATAL: Cannot connect to MySQL server on 'localhost'. Please make sure you have specified a valid MySQL database name in 'include/config.php' 

I have my /include/config.php set correctly - or atleast I set it to how I installed cacti. 

Cacti installation path is /var/www/cacti-0.8.7b/

I am going to paste my config.php file in here are well. 
*************************************************** 
<?php 
/* 
+-------------------------------------------------------------------------+ 
| Copyright (C) 2004-2008 The Cacti Group | 
| | 
| This program is free software; you can redistribute it and/or | 
| modify it under the terms of the GNU General Public License | 
| as published by the Free Software Foundation; either version 2 | 
| of the License, or (at your option) any later version. | 
| | 
| This program is distributed in the hope that it will be useful, | 
| but WITHOUT ANY WARRANTY; without even the implied warranty of | 
| MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the | 
| GNU General Public License for more details. | 
+-------------------------------------------------------------------------+ 
| Cacti: The Complete RRDTool-based Graphing Solution | 
+-------------------------------------------------------------------------+ 
| This code is designed, written, and maintained by the Cacti Group. See | 
| about.php and/or the AUTHORS file for specific developer information. | 
+-------------------------------------------------------------------------+ 
| [http://www.cacti.net/](http://www.cacti.net/) | 
+-------------------------------------------------------------------------+ 
*/ 

/* make sure these values refect your actual database/host/user/password */ 
$database_type = "mysql"; 
$database_default = "cacti"; 
$database_hostname = "localhost"; 
$database_username = "cacti"; 
$database_password = "*14msgwan!!"; 
$database_port = "3306"; 

/* Default session name - Session name must contain alpha characters */ 
#$cacti_session_name = "Cacti"; 

?> 
~ 

Can someone help the new guy learn. If there are some special commands you want me to execute so you can get a better feel of what I have installed just let me know. 

i386 PC 
Kubuntu 8.04 
Firefox 3.0 

I do have smokeping running and it works just fine..... 

Please any help would be greatly appreciated. Thanks Brandon

---

### Post by russlar on 2008-10-02
try altering the 'localhost' entry to '127.0.0.1'

---

### Post by bolds on 2008-10-02
Changed my /include/config.php 

now has $database_hostname = "127.0.0.1";  instead of localhost.

It did change something.  I don't get the error message, but at the same time it doen't load anything.  

Here is a copy of my /etc/crontab file...  Thought it have something to do with it...


# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
*/5 * * * cacti php /var/www/cacti-0.8.7b/

If anyone would like to see more let me know.  Thanks, Brandon

---

### Post by Trexpsy on 2009-10-15
I solved this by purging cacti and installed it again. Be sure to choose the correct httpd (apache2) 

apt-get purge cacti 
rm /etc/cacti -rf 
rm /usr/share/cacti -rf 
apt-get install cacti (choose apache2)

---

### Post by deathvoice on 2010-10-18
thanks it worked

---

### Post by ionospheric on 2013-02-12
> **Trexpsy said:**
> I solved this by purging cacti and installed it again. Be sure to choose the correct httpd (apache2) 

apt-get purge cacti 
rm /etc/cacti -rf 
rm /usr/share/cacti -rf 
apt-get install cacti (choose apache2)

That worked for me, too. Mostly because the first time, I used software center, and it never asked me for a password. Your method uses the command line, and that worked. Thanks.

---

