---
title: "Problem installing and configuring suPHP on Ubuntu 8.04 LTS"
date: 2008-10-01
forum: General Help
---

### Post by DirtyMonkey on 2008-10-01
I have followed taken instruction from the following sources but still suPHP fails to work.
I believe it may be specific to Debian/Ubuntu but I'm not sure. 
End result is that browser tries to download .php page instead of Apache processing it.

   Do I actually need to re-compile suPHP?
   Have I included a step which is not required?
   Have I missed something specific to Debian?
   What logs should I be checking for errors?

NB: I am using Plesk not ISPConfig (I don't think it makes a difference)

[http://www.howtoforge.com/apache2_suphp_php4_php5](http://www.howtoforge.com/apache2_suphp_php4_php5)
[http://www.howtoforge.com/install-suphp-on-various-linux-distributions-for-use-with-ispconfig-2.2.20-and-above](http://www.howtoforge.com/install-suphp-on-various-linux-distributions-for-use-with-ispconfig-2.2.20-and-above)
[http://www.howtoforge.com/forums/archive/index.php/t-13544.html](http://www.howtoforge.com/forums/archive/index.php/t-13544.html)

1. Disabled the normal PHP5 module:

> a2dismod php5
/etc/init.d/apache2 restart

2. Installed the prerequisites needed to build mod_suphp:

> apt-get install php5-cgi apache2-prefork-dev

3. Downloaded and built suPHP, adding the extra option ```
'--sbindir=/usr/lib/suphp':

```
> cd /tmp
wget [http://www.suphp.org/download/suphp-0.6.3.tar.gz](http://www.suphp.org/download/suphp-0.6.3.tar.gz)
tar xvfz suphp-0.6.3.tar.gz
cd suphp-0.6.3
./configure --prefix=/usr --sysconfdir=/etc --with-apache-user=www-data --with-setid-mode=paranoid --with-apxs=/usr/bin/apxs2 --sbindir=/usr/lib/suphp
make
make install

4. Added the suPHP module to Apache configuration:

> nano /etc/apache2/httpd.conf
```
LoadModule suphp_module       /usr/lib/apache2/modules/mod_suphp.so
```

5. Created the configuration file /etc/suphp.conf

> cp /tmp/suphp-0.6.3/doc/suphp.conf-example /etc/suphp.conf

```
[global]
;Path to logfile
logfile=/var/log/suphp.log

;Loglevel
loglevel=info

;User Apache is running as
webserver_user=www-data

;Path all scripts have to be in
docroot=/

;Path to chroot() to before executing script
;chroot=/mychroot

;Security options
allow_file_group_writeable=false
allow_file_others_writeable=false
allow_directory_group_writeable=false
allow_directory_others_writeable=false

;Check whether script is within DOCUMENT_ROOT
check_vhost_docroot=true

;Send minor error messages to browser
errors_to_browser=false

;PATH environment variable
env_path=/bin:/usr/bin

;Umask to set, specify in octal notation
umask=0077

;Minimum UID
min_uid=100

;Minimum GID
min_gid=100


[handlers]
;Handler for php-scripts
x-httpd-php=php:/usr/bin/php5-cgi

;Handler for CGI-scripts
x-suphp-cgi=execute:!self
```

6. Add the suPHP module to the Apache configuration.

> nano /etc/apache2/httpd.conf
```
LoadModule suphp_module       /usr/lib/apache2/modules/mod_suphp.so
```

7. Created hosts.conf file:

```
# PHP version detected 5
<IfModule mod_suphp.c>
<Directory "/var/www/vhosts/example.com/httpdocs/">
php_admin_flag engine on
suPHP_Engine On
suPHP_ConfigPath "/var/www/vhosts/example.com/httpdocs/"
AddHandler php5-script .php
AddHandler x-httpd-php .php5
suPHP_AddHandler php5-script .php
<Files php.ini>
order allow,deny
deny from all
</Files>
php_value open_basedir "/tmp/"
php_value upload_tmp_dir "/var/www/vhosts/example.com/httpdocs/tmp/"
</Directory>
</IfModule>
```

8. Restarted Apache:

> /etc/init.d/apache2 restart

---

### Post by jrbrownusa on 2010-05-18
You need to change this section of code in your /etc/suphp/suphp.conf

[handlers]
;Handler for php-scripts
x-httpd-php=php:/usr/bin/php5-cgi

;Handler for CGI-scripts
x-suphp-cgi=execute:!self

[B][handlers]
;Handler for php-scripts
application/x-httpd-suphp="php:/usr/bin/php-cgi"

;Handler for CGI-scripts
x-suphp-cgi="execute:!self"[/B]

Please note the quotes in the lines of codes.

Save restart apache Have fun!

---

