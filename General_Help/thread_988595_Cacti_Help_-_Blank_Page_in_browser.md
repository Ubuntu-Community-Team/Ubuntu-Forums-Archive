---
title: "Cacti Help - Blank Page in browser"
date: 2008-11-20
forum: General Help
---

### Post by bolds on 2008-11-20
I am looking for some help.  I have been going at this for about a month to no avail.  I know that the solution will seem very simple once it's solved.

My issue is - When I point my browser to 

[http://10.60.100.53/cacti](http://10.60.100.53/cacti)   --- I get nothing - blank page

I can go to 10.60.100.53  -- I get the defualt.html  --"It Works" page

I created a php test page called "info.php"  I placed several copies in the folder structure to test my apache and php.  

When I open [http://10.60.100.53/cacti/info.php](http://10.60.100.53/cacti/info.php)  --- It works, I get the php page.

If I put it in 10.60.100.53/info.php - again it works
If I put it in 10.60.100.54/cacti/install/info.php - again it works.


But if I go to the 10.60.100.53/cacti  -- I get a blank page

Here is a copy of my Apache2/log/error.log file
[Thu Nov 20 11:37:26 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/msql.so' - /etc/php5/apache2/php.ini/msql.so: cannot open shared object file: Not a directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/pdo.so' - /etc/php5/apache2/php.ini/pdo.so: cannot open shared object file: Not a directory in Unknown on line 0
[Thu Nov 20 11:37:26 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 20 11:54:10 2008] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/msql.so' - /etc/php5/apache2/php.ini/msql.so: cannot open shared object file: Not a directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/pdo.so' - /etc/php5/apache2/php.ini/pdo.so: cannot open shared object file: Not a directory in Unknown on line 0
[Thu Nov 20 11:54:21 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 20 13:22:34 2008] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/msql.so' - /usr/lib/php5/20060613+lfs/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Thu Nov 20 13:22:44 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 20 13:36:59 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Nov 20 13:37:09 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 20 13:40:31 2008] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/msql.so' - /usr/lib/php5/20060613+lfs/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Thu Nov 20 13:40:41 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Nov 20 13:45:19 2008] [notice] caught SIGWINCH, shutting down gracefully
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/msql.so' - /etc/php5/apache2/php.ini/msql.so: cannot open shared object file: Not a directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/etc/php5/apache2/php.ini/pdo.so' - /etc/php5/apache2/php.ini/pdo.so: cannot open shared object file: Not a directory in Unknown on line 0
[Thu Nov 20 13:45:29 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations


I can add or send any file that you guys will need to see in order to help me out.  Anything will be greatly appreciated.  Thanks, Brandon

---

### Post by adaptr on 2008-11-20
Your php.ini is either corrupt or missing entirely (not found by mod_php5).
Try a re-install of mod_php - in what order did you install cacti and all dependecies ?

---

### Post by bolds on 2008-11-20
Your php.ini is either corrupt or missing entirely (not found by mod_php5).
Try a re-install of mod_php - in what order did you install cacti and all dependecies ?


How do I check to see if my php.ini is corrupt or not?  

As far as order of install - I pretty much did this:

apt-get install mysql-server apache2 libapache2-mod-php5 php5-mysql php5-cli php5-snmp

And then went back and it 
Apt-get install cacti

Let me know if you need to see anything else.  Thanks for the help so far.....

---

